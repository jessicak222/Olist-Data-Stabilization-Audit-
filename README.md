# Olist-Data-Stabilization-Audit
**Technical Objective:** Neutralizing a Global Price Skew of 7.7 in the Olist dataset to stabilize revenue forecasting.

# Executive Summary
In the raw Olist e-commerce dataset, extreme price anomalies created a Global Price Skew of 7.7, rendering standard metrics like Average Order Value (AOV) and revenue forecasts unreliable.

This technical snippet demonstrates a Category-Specific Stabilization Pipeline designed to neutralize statistical noise while preserving 91% of organic high-value transaction volume. By applying localized 3xIQR caps, I successfully reduced the global skew to 4.4 and compressed data variance by 35%.

### Technical Highlights
- **SQL Architecture:** Engineered 4-table relational joins in BigQuery to map transaction costs to product metadata, ensuring a granular "Item-level" grain for analysis.

- **Split-Stream Processing:** Developed a custom Python engine that separates categorized and uncategorized entries into independent stabilization streams before recombination.

- **Statistical Winsorization:** Applied 3xIQR thresholds at the category level to identify and cap "Ultra-Outliers" (reaching 77x the median) without deleting valuable business data.

- **Visual Auditing:** Created comparative distribution overlays (Boxplots) and automated exception reports to validate stabilization impact.

Metric,Before Audit,After Stabilization,Impact
Global Skewness,7.7,4.4,43% Reduction
Standard Deviation,$189,$123,35% Volatility Decrease
Max Item Price,"$6,735","$3,450",50% Range Compression
Revenue Preserved,100%,91%,"$1.3M in ""Noise"" Neutralized"

# Repository Contents
olist_stabilization_audit.ipynb: The core technical narrative, featuring SQL queries, Python logic, and visual audits.

visual_summary_deck.pdf: A high-impact "Data Proof" document featuring annotated charts for non-technical stakeholders.

data/: Directory containing category limit references and stabilization logs.

# How to View
Directly on GitHub: Click the .ipynb file above to view the rendered code and charts.

Interactive via Colab: [Insert Link to your Colab Notebook here] for the full formatted experience.

