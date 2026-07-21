Quantium Data Analytics — Virtual Experience Program (Forage)

This repository documents my work completing Quantium's Data Analytics Virtual Experience Program via Forage, a self-paced program simulating real analyst work on Quantium's retail analytics team.

Note: the raw datasets provided by Forage/Quantium are not included in this repository, as they are proprietary. This repo contains my own analysis code, cleaned output data, and written findings.

Business Context

Acting as a data analyst on Quantium's retail analytics team, I was engaged by a client's Category Manager for chips to understand customer purchasing behaviour within the chip category, with insights intended to feed into the client's strategic plan for the category over the next six months.

Task 1: Data Preparation and Customer Analytics

Objective: Clean and prepare transaction and customer datasets, engineer relevant features, and analyse customer segments to identify who drives chip category sales and why.

Tools: Python (pandas, matplotlib), Google Colab

Data Cleaning


Removed 1 exact duplicate transaction row
Excluded a loyalty card account with two 200-unit purchases of the same product, consistent with a commercial/bulk buyer rather than a retail customer
Removed 7 salsa dip products incorrectly included in the transaction data (while retaining genuine salsa-flavoured chip products)
Converted the transaction date field from Excel serial format to calendar dates; confirmed the dataset spans 1 July 2018 – 30 June 2019, with no transactions on 25 December 2018 (store closure)
Engineered two new features from unstructured product name text: pack size and brand, correcting for case-sensitivity issues and 8 inconsistent brand spellings/abbreviations
Merged transaction and customer datasets on loyalty card number (249,667 rows, zero unmatched records)


Key Findings


Total sales are not the same as customer value. The segment with the highest total sales (Older Families/Budget) ranks highly partly due to segment size, not spending behaviour alone.
Families are the highest-value customers per capita. When normalised by number of customers, all six Family segments (Older and Young, across Budget/Mainstream/Premium tiers) rank in the top 6 of 20 segments for average spend per customer — despite the largest customer base overall (Young Singles/Couples, Mainstream) ranking near the bottom per customer.
The driver is purchase frequency, not basket size. Family segments purchase ~4.5–4.8 times per year on average, versus 2.4–3.6 for Singles/Couples and Retiree segments. Average units per transaction and average pack size are both essentially flat across all segments, ruling out "bigger baskets" or "bigger packs" as explanations.
Kettle is the dominant brand across every segment, indicating a stocking baseline rather than a segment-specific targeting lever.


Commercial Recommendation

The data supports prioritising Family segments (Older and Young, regardless of spend tier) for the chip category strategy, with promotional focus on increasing purchase frequency — e.g. loyalty or repeat-visit incentives — rather than pack-size or premium-tier plays, since neither meaningfully differentiates high-value from low-value segments in this data.

Repository Contents


Task1_QVI_Analysis.ipynb — full analysis notebook (data cleaning, feature engineering, segmentation, visualisation)
QVI_Task1_Report.pdf — exported report as submitted to Forage
QVI_data_cleaned.csv — cleaned, merged dataset produced by the analysis
