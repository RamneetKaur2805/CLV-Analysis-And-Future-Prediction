# Customer Lifetime Value (CLV) Analysis and Future Spending Prediction

## Project Overview
This project focuses on analysing customer behaviour, segmenting customers based on their purchasing patterns, and predicting future customer spending using machine learning regression models.

The main goal is to help businesses identify high-value customers, improve retention strategies, and maximize Customer Lifetime Value (CLV).

---

## 1. Business Problem Understanding

### What is Customer Lifetime Value (CLV)?
Customer Lifetime Value (CLV) refers to the total revenue a business expects to earn from a customer throughout their entire relationship with the company.

A customer who purchases repeatedly over several years has a much higher CLV than a one-time buyer.

---

### Why Increasing LTV is Important
Increasing Customer Lifetime Value is important because:

- Higher profitability from existing customers
- Lower acquisition costs over time
- Improved customer loyalty
- Better long-term revenue stability
- Higher return on customer acquisition investment

When customers spend more frequently and remain loyal longer, overall business revenue increases significantly.

---

### LTV vs One-Time Sales
#### One-Time Sales
- Focus only on immediate revenue
- No guarantee of repeat purchases
- Higher dependency on new customers

#### Customer Lifetime Value
- Focus on long-term revenue generation
- Encourages repeat purchases
- Builds stronger customer relationships
- More sustainable business growth

Example:
- Customer A buys once for $100
- Customer B buys $50 every month for 3 years

Customer B has significantly higher CLV.

---

### Why Existing Customers Are More Efficient Than New Customers
Acquiring new customers is often expensive due to:

- Advertising costs
- Promotions
- Sales efforts
- Discounts

Retaining existing customers is usually cheaper because:

- They already trust the brand
- Higher conversion probability
- Easier upselling and cross-selling
- Better response to loyalty programs

Research commonly shows retaining customers costs less than acquiring new ones.

---

### How Future Spending Prediction Helps Business
Predicting future spending allows businesses to:

- Identify high-value customers early
- Personalize offers
- Improve retention campaigns
- Forecast future revenue
- Allocate marketing budget efficiently
- Reduce customer churn risk

Businesses can proactively target customers likely to generate high future revenue.

---

## 2. Dataset Understanding

Dataset contains customer demographics, purchase history, engagement behaviour, and spending patterns.

---

### Important Columns Description

| Column Name | Meaning |
|---|---|
| CustomerID | Unique customer identifier |
| Age | Customer age |
| AnnualIncome | Annual income of customer |
| WebsiteVisits | Number of website visits |
| AppSessions | Number of mobile app sessions |
| PreviousOrders | Number of previous purchases |
| AverageOrderValue | Average value per order |
| DaysSinceLastPurchase | Days since last purchase |
| ReturnRate | Percentage of returned products |
| CancellationRate | Order cancellation percentage |
| LoyaltyTier | Customer loyalty level |
| DiscountUsedLastCampaign | Whether discount was used previously |
| Year1Spending | Spending in first year |
| FutureSpending | Expected future spending (target variable) |

---

### Customer Behaviour Columns
These columns represent engagement and purchasing behaviour:

- WebsiteVisits
- AppSessions
- PreviousOrders
- DaysSinceLastPurchase
- DiscountUsedLastCampaign

These indicate how actively customers interact with the business.

---

### Customer Value Columns
These represent customer monetary contribution:

- AverageOrderValue
- Year1Spending
- FutureSpending
- AnnualIncome

These help measure customer profitability.

---

### Features Influencing Future Spending
Potential predictors:

- PreviousOrders
- AverageOrderValue
- Year1Spending
- WebsiteVisits
- AppSessions
- LoyaltyTier
- ReturnRate
- CancellationRate
- DaysSinceLastPurchase

Customers with strong historical engagement are more likely to spend more in future.

---

### Target Variable
**FutureSpending** is used as the target variable.

Reason:
- Business wants to predict future customer revenue.

---

### Why This is a Regression Problem
This is a regression problem because:

- Target variable is continuous numerical value
- FutureSpending can be any number (e.g., 1500, 3500, 7200)

Unlike classification, we predict an exact numeric outcome.

---

## 3. Data Cleaning and Feature Engineering

### Data Cleaning
Performed:

- Missing value detection
- Missing numerical values filled using median
- Duplicate checking
- Data type correction
- Outlier visualization using boxplots

---

### Feature Engineering
New features created:

#### TotalOrders
Derived from:
- PreviousOrders

#### VisitFrequency
Calculated as:
WebsiteVisits + AppSessions

Helps capture overall engagement frequency.

#### EngagementScore
Combines:
- Website activity
- App activity
- Order frequency

Measures customer engagement intensity.

### Spending Growth
Difference of:
- FutureSpending
- Year1Spending

Measures the growth of the customer

---

## 4. Exploratory Data Analysis (EDA) Insights

Key findings:

### Spending Distribution
- Year1Spending is right-skewed
- FutureSpending is right-skewed

Most customers spend lower amounts while few high-value customers spend significantly more.

---

### Income vs Spending
Positive relationship observed:

- Higher AnnualIncome → Higher spending

---

### Year1Spending vs FutureSpending
Strong positive correlation found:

- Customers who spent more in Year 1 tend to spend more in future

This is one of the strongest predictors.

---

### PreviousOrders vs FutureSpending
Customers with higher order frequency show higher future spending.

---

### Outliers
High-value customers detected in FutureSpending.

These may represent premium customers.

---

## 5. Customer Segmentation Summary

Customer segmentation performed using:

- **K-Means Clustering**

Features used:

- Demographics
- Engagement behaviour
- Spending patterns
- Loyalty information

Optimal clusters determined using:

- **Elbow Method**

Clusters identified:

    **0: Segment A:** ( Low Value, Low Engagement),
    **1: Segment B:** ( High Value, High Engagement),
    **2: Segment C:** ( Medium Value, High Potential),
    **3: Segment D:** ( At-Risk, Discount Seekers)

Segmentation helps create personalized marketing strategies.

---

## 6. Regression Model Summary

Models used:

### 1. Linear Regression
Simple baseline regression model.

Advantages:
- Interpretable
- Fast training

---

### 2. Decision Tree Regressor
Captures non-linear relationships.

Advantages:
- Better pattern learning
- Handles feature interactions

---

## 7. Model Evaluation Results

Metrics used:

- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- R² Score

### Linear Regression Model Performance:

| Column Name | Figures |
|---|---|
| Mean Absolute Error (MAE) | 1058.77 |
| Mean Squared Error (MSE) | 1815990.06 |
| Root Mean Squared Error (RMSE) | 1347.59 |
| R2 Score | 0.91 |

### Decision Tree Regressor Model Performance:

| Column Name | Figures |
|---|---|
| Mean Absolute Error (MAE) | 1640.87 |
| Mean Squared Error (MSE) | 4247385.83 |
| Root Mean Squared Error (RMSE) | 2060.92 |
|R2 Score | 0.80 |

**The Linear regression model outperforms the Decision tree regressor model**

---

## Business Recommendations Based on Customer Segmentation and LTV Prediction

Based on the customer segmentation and the future spending predictions, here are strategic recommendations tailored for each segment:


### Segment B: High Value, High Engagement Customers

*   **Characteristics**: Likely show high Annual Income, high Website Visits/App Sessions, many Previous Orders, and high Year 1 Spending, leading to high predicted Future Spending.

* #### Which customers should receive premium offers?
    *   **Segment B** customers are ideal for premium offers. Their high engagement and past spending indicate a willingness to invest in high-quality products or exclusive services. Focus on retaining their loyalty and increasing their share of wallet.

*   **Which customers should be targeted for upselling?**
    *   **Segment B** customers are prime candidates for upselling. Introduce them to higher-tier products, subscription services, or bundled offerings that complement their past purchases and align with their demonstrated high spending capacity.

*   **How can the company increase overall LTV?**
    *   For Segment B, focus on **loyalty programs, exclusive access, personalized recommendations** for premium products, and **excellent customer service** to maintain their high engagement and prevent churn. Their high LTV is crucial for overall company growth.

### Segment C: Medium Value, High Potential Customers

*   **Characteristics**: May have moderate spending but exhibit growing engagement or specific behaviors that suggest future growth (e.g., increasing Website Visits, recent purchases after a long gap).

*   **Which customers should receive premium offers?**
    *   Selected customers within **Segment C** who show a positive trend in engagement or spending growth (as indicated by the `SpendingGrowth` feature) could be offered curated premium trials or introductory premium offers to nudge them towards higher-value tiers.

*   **Which customers should be targeted for upselling?**
    *   **Segment C** customers should be gently targeted for upselling. Offer personalized suggestions based on their current purchasing patterns, perhaps with a slight incentive to encourage them to explore higher-value items or services.

*   **How can the company increase overall LTV?**
    *   For Segment C, the strategy should be to **nurture and grow their spending**. Utilize personalized marketing, showcase the benefits of becoming a high-value customer, and offer incentives for repeat purchases or engagement.

### Segment D: At-Risk, Discount Seekers

*   **Characteristics**: Likely show higher `ReturnRate` or `CancellationRate`, longer `DaysSinceLastPurchase`, or primarily engage with discounts, leading to lower or declining `FutureSpending` predictions.

*   **Which customers should receive discounts?**
    *   **Segment D** customers are the primary candidates for targeted discounts. These should be strategic, perhaps tied to specific products they've shown interest in, or time-limited offers to re-engage them. The goal is to reactivate them and prevent churn, but carefully manage the discount strategy to avoid devaluing the brand.

*   **Which customers need re-engagement?**
    *   **Segment D** customers are most in need of re-engagement. Implement campaigns focusing on their specific needs or pain points, offering personalized solutions, or reminding them of the value they're missing. Emphasize new product launches or improvements that might address their past reasons for reduced engagement.

*   **Which customers should not receive expensive offers?**
    *   **Segment D** customers should generally not receive expensive offers unless the offer is specifically designed as a high-value re-engagement incentive with a clear ROI justification. Their current behavior suggests they are not likely to convert on full-priced premium items.

*   **How can the company increase overall LTV?**
    *   For Segment D, focus on **churn prevention and reactivation**. Targeted, value-driven discounts, personalized outreach, and surveys to understand their dissatisfaction are key. The goal is to prevent a complete loss of these customers and slowly move them towards higher engagement.

### Segment A: Low Value, Low Engagement Customers

*   **Characteristics**: Typically have low Annual Income, few Website Visits/App Sessions, minimal Previous Orders, low Year 1 Spending, and consequently low predicted Future Spending.

*   **Which customers should not receive expensive offers?**
    *   **Segment A** customers should definitively not receive expensive offers. Their low engagement and spending patterns indicate a low propensity to convert on such offers, making these marketing efforts inefficient and costly.

*   **How can the company increase overall LTV?**
    *   For Segment A, a **cost-effective strategy** is crucial. Broad, low-cost marketing campaigns to introduce them to basic offerings or entry-level products might be considered. Focus on acquisition of new, potentially higher-value customers rather than spending significant resources on drastically increasing the LTV of this segment, unless a scalable, low-cost strategy can be identified.

### Overall Company Strategy to Increase LTV
1.  **Prioritize High-Value Segments**: Dedicate the most resources and personalized attention to **Segment B** to maximize their retention and continued growth.

2.  **Nurture High-Potential Segments**: Invest in **Segment C** with targeted campaigns and incentives to move them into higher-value tiers.

3.  **Strategic Re-engagement**: For **Segment D**, use data-driven, personalized re-engagement strategies, including selective discounts, to prevent churn and gently nudge them towards more valuable behaviors.

4.  **Efficient Resource Allocation**: Avoid costly campaigns for **Segment A**; focus on cost-effective awareness or mass-market approaches, or shift resources to higher-potential segments.

5.  **Personalization**: Leverage the `FutureSpending` prediction to tailor offers and communications at an individual customer level, even within segments, for maximum impact.

6.  **Continuous Monitoring**: Regularly re-evaluate segment characteristics and model performance to adapt strategies as customer behavior evolves.

---

# How to Run the Project

## Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/marketing-budget-optimization.git
```

---

## Step 2: Navigate to the Project Folder

```bash
cd CLV Analysis and future prediction
```

---

## Step 3: Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn sklearn
```

---

## Step 4: Launch Jupyter Notebook

```bash
jupyter notebook
```

---

## Step 5: Open the Notebook

Open:

```bash
Marketing_Budget_optimisation.ipynb
```

---
