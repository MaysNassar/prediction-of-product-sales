# **Prediction-Of-Product-Sales: A Data-Driven Approach to Inventory Optimization**
Optimize inventory and pricing strategies using predictive analytics of product-store-level sales
_________________________________________________________________________________
_________________________________________________________________________________

## Business Problem
BigMart operates 10 retail outlets across different regions and must forecast product-level sales to:
- Optimize inventory — avoid stockouts and overstock situations
- Improve pricing strategy — identify high-impact price points
- Allocate resources efficiently — understand which product-outlet combinations drive revenue

With 1,559 unique products and multiple store formats, manual forecasting is inefficient. This analysis builds a predictive model to estimate sales for each product at each outlet.
_________________________________________________________________________________

## Data Overview

- Dataset: BigMart sales data (2013)
- Records: 8,523 product-outlet transactions
- Products: 1,559 unique items across 16 categories
- Outlets: 10 stores in 3 location tiers (Tier 1/2/3 cities)
- Target Variable: Item-Outlet Sales (in dollars)
--------------------------------------------------------------------------
### Key Data Characteristics:

- 17% missing weight values (filled via product grouping)
- 28% missing outlet size (filled via mode)
- Categorical inconsistencies in fat content (cleaned)
_________________________________________________________________________________

## Key Insights
1. Price is the Dominant Sales Driver
   <img width="1390" height="490" alt="تنزيل (1)" src="https://github.com/user-attachments/assets/f5ee0c3e-d0fc-4267-a633-2fc9b74fb340" />

Item MRP shows the strongest correlation with sales (r = 0.57). Products are positioned at 4 distinct price tiers, and higher-priced items consistently generate higher revenue. However, price alone explains only 32% of sales variation, suggesting outlet characteristics and product type matter significantly.
Business Impact: Pricing optimization requires segmentation by product type and outlet format, not blanket adjustments.

2. Store Size and Location Type Create Distinct Sales Profiles
   
<img width="1389" height="490" alt="14" src="https://github.com/user-attachments/assets/f0307273-cb55-4c32-ae8e-bbb0a1a29b4c" />

Large outlets average 35% higher sales than small stores
Tier 1 locations (major cities) outperform Tier 3 by 20-25%
These effects compound: a large store in a Tier 1 city is substantially different from a small store in Tier 3

Business Impact: Sales forecasts must be outlet-specific, not product-generic. A product's forecast in a flagship store will be 40-50% higher than in a small neighborhood store.

 3. Feature Importance Comparison
  What Drives Sales Most?
<img width="990" height="590" alt="تنزيل" src="https://github.com/user-attachments/assets/ac4819ce-3155-4ce5-95de-db48b8dd51ee" />

_________________________________________________________________________________

## Modeling Approach
### Data Preprocessing

- Feature Engineering: Extracted outlet age, standardized categorical variables
- Handling Missing Data:
   - Item weights: Grouped by product ID (same product has the same weight)
   - Outlet size: Mode imputation (most common store size)

- Encoding: Ordinal encoding for size/location tiers; one-hot encoding for product types
------------------------------------------------------------------------------------
### Model Selection & Hyperparameter Tuning
Compared two approaches:
<img width="640" height="257" alt="image" src="https://github.com/user-attachments/assets/f3925f13-9a3a-485e-8330-e0bed9e78500" />

- Final Model: Random Forest with max_depth=15, min_samples_leaf=5, n_estimators=200
_________________________________________________________________________________
### Model Performance & Reliability
#### What This Means:
- For a product with actual sales of $2,000, the model predicts $1,250–$2,750 (±$750 range)
- The model is reliable for strategic decisions (ranking products, identifying underperformers) but not for exact forecasts
- Remaining unexplained variance (~41%) likely reflects seasonal trends, promotions, and local factors not in the dataset

_________________________________________________________________________________
_________________________________________________________________________________

## Recomendations
**Smart Steps for BigMart Inventory & Pricing**
Our analysis of BigMart's sales data gives us some great insights to help you optimize inventory and pricing.

1. Use predictions for segmentation, not exact forecasts
   Rank products/outlets by predicted sales to identify high-potential combinations
   Focus inventory investments on the top predicted performers


2. Augment with external data.
   Seasonal indices, promotional calendars, and local events
   Competitor pricing and weather data would improve accuracy

3. Monitor and retrain quarterly.
   Consumer preferences and pricing strategies change
   Retrain the model with new sales data to maintain accuracy


4. Deploy as decision support, not automation.
   Use predictions to guide human planners, not replace them
   A $750 error margin is meaningful; validate high-stakes decisions manually
____________________________________________________________________________________________________________________________________________________________________________
sales_prediction_model.ipynb — Complete analysis: data cleaning, EDA, modeling, evaluation
