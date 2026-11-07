# Hotel Reviews & Customer Experience Analytics

### Business Intelligence and Data Analytics with Microsoft Power BI

An independent data analytics project focused on understanding hotel customer experiences, identifying recurring complaints, evaluating hotel performance, and transforming customer feedback into actionable business insights.

This project demonstrates how data analytics and business intelligence can support decision-making in the hospitality industry.

---

## Project Overview

Customer reviews contain valuable information about service quality, customer satisfaction, and operational performance.

The objective of this project is to analyze hotel customer reviews and develop an interactive Power BI dashboard that helps identify sentiment patterns, recurring customer complaints, and differences in hotel performance.

The project focuses on the analytical and business intelligence layer of a larger data engineering workflow.

## Dashboard Preview

### 1. Executive Overview

![Executive Overview](screenshots/Screenshot%201.png)

Provides a high-level overview of customer feedback, key performance indicators, and sentiment distribution.

### 2. Customer Complaints Analysis

![Customer Complaints Analysis](screenshots/Screenshot%202.png)

Explores recurring customer complaints and identifies the main areas affecting customer experience.

### 3. Hotel Performance Comparison

![Hotel Performance Comparison](screenshots/Screenshot%203.png)

Compares hotel performance using customer sentiment and complaint-related indicators.

---

## Business Questions

This project addresses the following business questions:

1. What is the overall distribution of positive, negative, and neutral customer reviews?
2. Which hotels receive the highest proportion of negative feedback?
3. What are the most frequently reported customer complaints?
4. Which complaint categories have the greatest impact on customer experience?
5. How does customer sentiment differ between hotels?
6. Which areas should hotel management prioritize for service improvement?

## Key Analytical Areas

### Customer Sentiment Analysis
- Distribution of positive, negative, and neutral reviews.
- Identification of negative customer feedback.
- Comparison of sentiment across hotels.

### Customer Complaint Analysis
- Identification of recurring complaint categories.
- Analysis of frequently mentioned negative phrases, overall and per hotel.
- Comparison of complaint patterns across hotels.

### Hotel Performance Analysis
- Hotel-level performance comparison.
- Identification of hotels with higher negative feedback, using a minimum sample threshold (30+ reviews) to avoid small-sample bias.
- Evaluation of customer experience indicators.

### Business Intelligence Reporting
- Interactive dashboard development.
- KPI monitoring.
- Comparative analysis.
- Data-driven business recommendations.

---

## Technical Skills & Tools

| Area | Technologies / Skills |
|---|---|
| Business Intelligence | Microsoft Power BI |
| Data Visualization | Power BI Charts and Visuals |
| Data Analysis | Python, Pandas |
| Data Modeling | Fact and Dimension Tables |
| Analytical Calculations | DAX |
| Reporting | KPI Development and Interactive Dashboards |
| Business Analysis | Customer Experience and Performance Analysis |

---

## Data Model

The analytical datasets follow a structured approach using fact and dimension tables. Tables are related through `hotel_id` (hotel level) and `review_id` (review level), never through hotel names.

Key datasets include:

- `dim_hotels`: Hotel dimension information.
- `fact_reviews`: Review-level analytical data.
- `fact_review_complaint_categories`: Complaint categories assigned to individual reviews.
- `fact_hotel_sentiment_summary`: Hotel-level sentiment summaries.
- `fact_hotel_complaint_summary`: Hotel-level complaint summaries.
- `fact_hotel_negative_phrases`: Most frequent negative phrases per hotel.
- `fact_hotel_top_phrase_matrix`: Top negative phrases compared across hotels.
- `fact_overall_negative_phrases` and `fact_overall_negative_phrases_v2`: Most frequent negative phrases across all hotels (two versions).
- `data_quality_summary`: Summary of data quality checks.

See the `documentation/` directory for additional information about the data model and analytical methodology.

## Repository Structure

```text
hotel-reviews-business-analytics/
│
├── README.md
│
├── dashboard/
│   ├── Hotel Complaints & Performance Analysis1.pbix
│   └── Hotel Complaints & Performance Analysis-.pdf
│
├── screenshots/
│   ├── Screenshot 1.png
│   ├── Screenshot 2.png
│   └── Screenshot 3.png
│
├── data/
│   ├── data_quality_summary.csv
│   ├── dim_hotels.csv
│   ├── fact_hotel_complaint_summary.csv
│   ├── fact_hotel_negative_phrases.csv
│   ├── fact_hotel_sentiment_summary.csv
│   ├── fact_hotel_top_phrase_matrix.csv
│   ├── fact_overall_negative_phrases.csv
│   ├── fact_overall_negative_phrases_v2.csv
│   ├── fact_review_complaint_categories.csv
│   └── fact_reviews.csv
│
├── dax/
│   └── dax_measures_en.txt
│
└── documentation/
    ├── business_questions.md
    ├── data_model.md
    └── key_insights.md
```

## How to Explore the Project

1. Browse the dashboard screenshots above.
2. Download the Power BI `.pbix` file.
3. Open the file using Microsoft Power BI Desktop.
4. Explore the interactive reports, filters, visualizations, and DAX measures.
5. Review the documentation and analytical datasets.

### Dashboard Files

- [Power BI Dashboard](dashboard/Hotel%20Complaints%20%26%20Performance%20Analysis1.pbix)
- [Dashboard PDF](dashboard/Hotel%20Complaints%20%26%20Performance%20Analysis-.pdf)
- [DAX Measures](dax/dax_measures_en.txt)

### Documentation

- [Business Questions](documentation/business_questions.md)
- [Data Model](documentation/data_model.md)
- [Key Insights](documentation/key_insights.md)

---

## Business Value

The analysis can help hotel management:

- Understand customer satisfaction patterns.
- Identify recurring service problems.
- Compare customer experience across hotels.
- Prioritize operational improvements.
- Monitor customer feedback using measurable indicators.

The dashboard is intended as a decision-support tool rather than a substitute for operational investigations.

## Related Project: Data Engineering Pipeline

This analytics project is connected to a separate end-to-end data engineering project.

**Original Repository:**

[Hotel Reviews Data Engineering & Analytics Pipeline](https://github.com/YasserEA/hotel-reviews-data-engineering)

The original project covers data ingestion, processing, sentiment classification, and analytical dataset generation.

This repository focuses specifically on Business Intelligence, data analysis, DAX, and Power BI reporting.

---

## Author

**Yasser Eid Khalifa**

Data Analytics | Business Intelligence | Mathematical & Statistical Modeling

GitHub: [YasserEA](https://github.com/YasserEA)

---

*This is an independent portfolio project developed for educational and professional demonstration purposes.*
