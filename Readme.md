# Project Deliverable 3: Classification, Clustering, and Pattern Mining

**Student:** Sandeep Parupalli  
**Course:** 2026 Spring - Advanced Big Data and Data Mining (MSCS-634-B01)  
**Instructor:** Satish Penmatsa  
**Repository Link:** https://github.com/Sandeep271/Project-Deliverable-3-Classification-Clustering-and-Pattern-Mining

## Dataset Summary
This deliverable uses the Online Retail dataset. The original file contains transactional records from an online gift retailer. After removing duplicates, missing customer and product descriptions, and non-positive quantity or price values, the cleaned data was aggregated to the customer level for classification and clustering tasks. Association rule mining was performed on the cleaned transaction-level data using the most frequent products.

## Files Included
- `MSCS_634_Project_Deliverable_3_Submission_Ready.ipynb`
- `README.md`
- `Sandeep_Parupalli_Project_Deliverable_3_Detailed_Report.docx`

## Modeling Process
### Classification
Two classification models were developed to identify high-value customers:
- Decision Tree
- k-NN

A binary target named `HighValueCustomer` was created using the median of customer spending. The predictors used were:
- number of transactions
- total quantity purchased
- average unit price
- number of active months

The Decision Tree was then tuned using `GridSearchCV`. The tuned model used:
- `max_depth = 5`
- `min_samples_split = 2`
- `min_samples_leaf = 1`

### Clustering
A K-Means clustering model with three clusters was built using standardized customer-level features:
- NumTransactions
- TotalQuantity
- AvgUnitPrice
- TotalSpent
- ActiveMonths

PCA was used to visualize the three customer groups.

### Pattern Mining
Apriori association rule mining was applied to the top 20 most frequent products. Rules were ranked by lift to highlight the strongest product combinations.

## Key Results
### Classification performance
- Decision Tree: Accuracy = 0.9067, F1 = 0.9089
- k-NN: Accuracy = 0.9171, F1 = 0.9182
- Tuned Decision Tree: Accuracy = 0.9182, F1 = 0.9205

The tuned Decision Tree performed best overall. Its cross-validation F1 score was 0.9273, which suggests the model generalizes well.

### Clustering insights
- Cluster 0 contains the largest group of lower-activity, lower-spending customers.
- Cluster 2 contains medium-value customers with stronger engagement and higher spending.
- Cluster 1 is a very small but extremely high-value group with much larger transaction counts and total spend.

### Pattern mining insights
The strongest rules show that several lunch bag products are frequently purchased together. The highest-lift rule in this deliverable was:

**LUNCH BAG PINK POLKADOT -> LUNCH BAG  BLACK SKULL., LUNCH BAG CARS BLUE**  
Support = 0.0241, Confidence = 0.2793, Lift = 7.1482

## Practical Relevance
These findings can support real business decisions:
- Classification can identify higher-value customers for retention or loyalty campaigns.
- Clustering can help segment customers for differentiated offers and messaging.
- Association rules can support product bundling, recommendation systems, and cross-selling strategies.

## Challenges and How They Were Addressed
- **Missing and invalid records:** cleaned by removing duplicates, missing descriptions, missing customer IDs, and non-positive quantity and price values.
- **Different feature scales:** addressed with standardization before k-NN and clustering.
- **Model tuning:** addressed with grid search to improve Decision Tree performance.
- **Association rule complexity:** managed by limiting the basket analysis to the top 20 most frequent products.

## Final Summary
Deliverable 3 shows that customer behavior in the Online Retail dataset can be analyzed successfully using classification, clustering, and pattern mining. The tuned Decision Tree produced the strongest classification results, K-Means revealed meaningful customer segments, and Apriori uncovered product combinations with clear merchandising value.
