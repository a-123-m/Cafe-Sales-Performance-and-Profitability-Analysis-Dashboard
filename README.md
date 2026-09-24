# ☕︎ Cafe-Sales-Performance-and-Profitability-Analysis-Dashboard
<p align="center">
<img width="764" height="441" alt="Gemini_Generated_Image_he93tjhe93tjhe93" src="https://github.com/user-attachments/assets/392ed949-39df-4e6b-9cda-03afba4fe5f1" />
</p>

## 📊 Project Overview
This dashboard was created in order to understand the overall sales performance, profitability, customer payment behavior and category wise product performance in a cafe. The dashboard transforms raw cafe sales data into an interactive business report that helps users understand overall performance, compare products, analyze costs and identify monthly profitability trends.

## 🎯 Business Objectives
The main objective of this project is to provide a single interactive view of cafe performance and answer important business questions such as:

- How much revenue is the cafe generating?
- How much gross profit is being generated?
- What is the average order value?
- Which products contribute the most to gross profit?
- How does product profitability change over time?
- What are the major cost components?
- How are customers paying for their orders?
- How does each product's gross profit change from month to month?

## 🖼️ Dashboard Preview
<img width="1432" height="801" alt="Screenshot 2026-09-24 103620" src="https://github.com/user-attachments/assets/2742644d-f3cc-4e77-8f5a-64d215c72f86" />

## 🎥 Dashboard Demo
https://github.com/user-attachments/assets/29792b50-9c34-45a9-89fc-13ee06629859

# 🔄 Project Workflow
The project was completed through the following data analytics workflow:
### 1. Data Collection
   Collected a cafe sales dataset that contains 3200+ records.
### 2. Data Inspection and Understanding
   The dataset was analyzed to understand each columns and their datatypes as well as the records stored in them. Used PowerQuery, to convert all the mixed date formats to a particular format.

   #### 📋 Dataset Column Description

| Column | Description |
|---|---|
| **Order_ID** | Unique identifier assigned to each order. |
| **Order_Date** | Date on which the order was placed. |
| **Month** | Month in which the order was placed. |
| **Year** | Year in which the order was placed. |
| **Category_Type** | Food category type |
| **Category** | Specific food category to which the item belongs. |
| **Item_Name** | Name of the food or beverage item ordered. |
| **Quantity** | Number of units of the item included in the order. |
| **Unit_Price_$** | Selling price of one unit of the item, in USD. |
| **Total_Amount_$** | Total sales amount generated from the order, in USD. |
| **Food_Cost_$** | Cost of ingredients or food materials used to prepare the order, in USD. |
| **Labour_Cost_$** | Labour cost associated with preparing or fulfilling the order, in USD. |
| **Profit_$** | Profit generated from the order after deducting relevant costs, in USD. |
| **Delivery_Partner** | Delivery service or partner responsible for delivering the order. |
| **Payment_Mode** | Payment method used by the customer to complete the order. |

### 3. Creation of KPI measures
   - Total Revenue

     > Total Revenue = SUM(cleaned_cafe_dataset[Total_Amount_$])
     
   - Previous month revenue

     > Previous month revenue = CALCULATE([Total Revenue],DATEADD('Calendar'[Date],-1,MONTH))
     
   - Revenue Growth %

     > Revenue Growth % = DIVIDE([Total Revenue]-[Previous month revenue],[Previous month revenue],0)
     
   - Gross Profit

     > Gross Profit = SUM(cleaned_cafe_dataset[Profit_$]) 
     
   - Previous month Gross Profit

     > Previous month profit = CALCULATE([Gross Profit],DATEADD('Calendar'[Date],-1,MONTH))
     
   - Profit Margin %

     > Profit Margin % = DIVIDE([Gross Profit],[Total Revenue],0)
     
   - Average Order Value (AOV)

     > Average Order Value (AOV) = DIVIDE([Total Revenue],[Total orders],0)
     
   - Previous month AOV

     > Previous month AOV = CALCULATE([Average Order Value (AOV)],DATEADD('Calendar'[Date],-1,MONTH))
     
   - AOV Growth %

     > AOV Growth % = DIVIDE([Average Order Value (AOV)]-[Previous month AOV],[Previous month AOV])
     
   - Cumulative Gross Profit %

    > VAR total_profit = CALCULATE([Gross Profit],ALL(cleaned_cafe_dataset[Item_Name]))
    > VAR current_profit = [Gross Profit]
    > VAR running_profit = CALCULATE([Gross Profit],FILTER(ALLSELECTED(cleaned_cafe_dataset[Item_Name]),[Gross Profit] >= current_profit))
    > RETURN DIVIDE(running_profit,total_profit,0)

   - Digital Payment Revenue

     > Revenue_DigitalPayment = CALCULATE([Total Revenue],cleaned_cafe_dataset[Payment_Mode] <> "Cash")
     
   - Digital payment %

     > Digital Payment % = DIVIDE([Revenue_DigitalPayment],[Total Revenue],0)
     
### 4. Creation of visuals
Different visuals like Line and clustered column chart, scatter plot, waterfall chart, pie chart and matrix were constructed to understand the overall cafe business sales and profit generated.

#### ★ Item-wise Gross Profit & Cumulative Gross Profit % - Line and clustered column chart
This visual compares gross profit generated by individual products and shows the cumulative contribution of those products.

#### ★ Overall Sales Performance - Scatter plot
The scatter chart compares products across the selected sales/performance measures. Each bubble represents quantity of product sold, allowing product-level performance to be compared visually.

#### ★ Cost Breakdown - Waterfall chart
The Waterfall Chart provides a step-by-step view of how different cost components affect the financial result.
The analysis includes cost components such as:
- Food Cost
- Labour Cost

#### ★ Revenue by Payment Mode - Pie chart
The donut chart shows the distribution across different payment methods - UPI, Online, Card and Cash

#### ★ Gross Profit Overview by Item & Month - Matrix
The matrix visual provides a monthly breakdown of gross profit for individual products.

### 5. Creation of final dashboard in PowerBI
Dashboard layout, color scheme and design was generated with the help of AI to give the dashboard a professional look. All the KPI metrics and visuals created were finally added along with interactive slicers, dynamic titles and bookmarks to create this PowerBI dashboard.

## 🔎 Key Insights
- The cafe generated $8.83K in total revenue, up from $8.03K last month, representing approximately 9.97% revenue growth.
- Gross Profit increased to $4.23K, compared with $3.84K last month, while the gross profit margin stood at approximately 47.92%.
- The Average Order Value (AOV) remained relatively stable at $25.07, compared with $25.16 last month, showing a slight decrease of approximately 0.34%.
- Within the Burger category, Veg Cheese Burger recorded the highest gross profit at $1,220.33, while Spicy Bean Burger recorded the lowest at $891 among the burger varieties.
- Veg Cheese Burger stands out as a strong-performing item in the Burger category, generating higher revenue and profit margin while also recording the highest quantity sold. In comparison, Spicy Bean Burger generated a reasonable amount of revenue but had a lower profit margin.
- The cost breakdown waterfall chart shows that food cost is the larger cost component compared with labour cost. Monitoring and managing food costs could help control direct expenses and support overall profitability.
- Digital payments (UPI, Online, and Card) are the most preferred payment methods, accounting for approximately 75.53% of transactions, while Cash contributes 24.74%.
- The Gross Profit by Item and Month analysis shows that October was a strong month for the Burger category, with Aloo Tikki Burger generating the highest gross profit of $186.69. In November, the same item generated $175.48 in gross profit. Veg Cheese Burger started with a lower gross profit but reached its highest monthly profit of $164.80 in December.

<p>If you found this project helpful, consider giving it a ⭐ on GitHub!<br> Thank you❤️</p>
<div>
  <h2>Connect with Me</h2>
<a href="mailto:aiswarya2000mohan@gmail.com">
  <img src="https://img.shields.io/badge/-Gmail-red?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail">
</a>
<a href="https://www.linkedin.com/in/aiswarya-mohan-950948221/">
  <img src="https://img.shields.io/badge/-LinkedIn-blue?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
</a>
</div>
