# Data Model

## Overview
The model is a star schema. `dim_hotels` is the single dimension; every fact table connects to it through `hotel_id`. Relationships use `hotel_id`, never the hotel name, to avoid mismatches and inconsistent totals.

## Tables

| Table | Grain (one row per) | Key columns |
|---|---|---|
| `dim_hotels` | hotel | `hotel_id`, `hotel` |
| `fact_reviews` | review | `review_id`, `hotel_id`, `rating`, `predicted_sentiment`, `confidence`, `prob_negative`, `prob_neutral`, `prob_positive`, `text`, `lang` |
| `fact_review_complaint_categories` | review and matched complaint category | `review_id`, `hotel_id`, `complaint_category` |
| `fact_hotel_sentiment_summary` | hotel | `hotel_id`, review counts by sentiment, percentages, average rating |
| `fact_hotel_complaint_summary` | hotel and complaint category | `hotel_id`, `complaint_category`, matched reviews, share of the hotel's negative reviews |
| `fact_hotel_negative_phrases` | hotel and phrase | `hotel_id`, `phrase`, `negative_review_count`, `rank` |
| `fact_overall_negative_phrases` | phrase (original single-word list) | `phrase`, `negative_review_count`, `rank` |
| `fact_overall_negative_phrases_v2` | phrase (two-word phrases) | `phrase`, `negative_review_count`, `pct_of_negative_reviews`, `rank` |
| `fact_hotel_top_phrase_matrix` | hotel and top-30 phrase | `hotel_id`, `hotel`, `phrase`, `negative_review_count` |
| `data_quality_summary` | metric | `metric`, `value` |

> Verify the column lists against your files (open each CSV and read the header row) before publishing.

## Relationships
All relationships are single direction, one-to-many from the dimension or phrase table.

| From (one) | To (many) | Column |
|---|---|---|
| `dim_hotels` | `fact_reviews` | `hotel_id` |
| `dim_hotels` | `fact_review_complaint_categories` | `hotel_id` |
| `dim_hotels` | `fact_hotel_top_phrase_matrix` | `hotel_id` |
| `fact_overall_negative_phrases_v2` | `fact_hotel_top_phrase_matrix` | `phrase` |

`data_quality_summary` is a standalone table.

```text
fact_overall_negative_phrases_v2 ──(phrase)──▶ fact_hotel_top_phrase_matrix ◀──(hotel_id)── dim_hotels ──▶ fact_reviews
```

## Key DAX measures
Full code in [`dax/dax_measures_en.txt`](../dax/dax_measures_en.txt).

| Measure | Definition |
|---|---|
| Total Reviews | Row count of `fact_reviews` |
| Positive / Negative Reviews | Reviews with the given `predicted_sentiment` |
| Positive % / Negative % | Share of total reviews |
| Average Rating | Average of `rating` across reviews |
| Complaint Mentions | Sum of phrase counts for the top 10 phrases |
| Hotel Mentions | Phrase counts per hotel for the phrases in the current filter |
| Hotels Affected | Distinct hotels with at least one mention of the filtered phrases |
| Hotel Share % | A hotel's share of all mentions in the current selection |

## Design decisions
- **30-review minimum** for hotel rankings, because percentages from very small samples are misleading.
- **Totals are turned off** in Top N tables, since a total over a subset is not comparable to a global KPI.
- **Phrase tables use two-word phrases** with stop words removed, because single words (for example *desk*, *went*) carry little meaning.
