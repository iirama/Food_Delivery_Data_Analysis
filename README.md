# Food Delivery Data Analysis - In Saudi Arabia (2022-2024) 🛵🍔📊

## 📌 Project Overview
This project analyzes food delivery data across major Saudi Arabian cities from 2022 to 2024. Discover customer behavior patterns, restaurant performance metrics, and business growth opportunities through data-driven insights!

## 📑 Dataset Structure
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 10000 entries, 0 to 9999
    Data columns (total 7 columns):
     #   Column                               Non-Null Count  Dtype  
    ---  ------                               --------------  -----  
     0   Order Number                         10000 non-null  int64  
     1   Order Date and Time                  10000 non-null  object 
     2   Order_City                           10000 non-null  object 
     3   Restaurant Type                      10000 non-null  object 
     4   Total Bill (in Saudi Riyals)         10000 non-null  float64
     5   Delivery Duration (in minutes)       10000 non-null  int64  
     6   Customer Rating (from 1 to 5 stars)  10000 non-null  int64  
    dtypes: float64(1), int64(3), object(3)
    memory usage: 547.0+ KB

### 7 Columns and 10k Rows
🟢 No missing values in any column (100% complete)

⚠️ Type conversions performed:

1. Order Date and Time converted from object to datetime.
2. Created new time-based features during analysis.

## 🧹 Data Cleaning Process
```python
# Convert to datetime
df['Order Date and Time'] = pd.to_datetime(df['Order Date and Time'])

# Extract time features
df['Order Year'] = df['Order Date and Time'].dt.year
df['Order Month'] = df['Order Date and Time'].dt.month_name()
df['Month_Year'] = df['Order Date and Time'].dt.strftime('%b %Y')
df['Time_of_Day'] = df['Order Date and Time'].dt.strftime('%p')

# Filter years
df = df[df['Order Year'].between(2022, 2024)]
```

## 🖇️ Correlation Analysis

### 📊 Understanding Data Relationships
This section examines how different numerical variables in the dataset relate to each other.

**Correlation Coefficients Explained**:
- ➕ **+1**: Strong positive relationship (variables increase together)
- ➖ **-1**: Strong negative relationship (one increases as other decreases)
- 🔘 **0**: No linear relationship

![image](https://github.com/user-attachments/assets/ceecd439-bbc6-4329-bb9c-7586879ac7a6)



### 🌡️ Correlation Heatmap Insights
The heatmap visualizes relationships between:
1. 💵 Total Bill (SAR)
2. ⏱️ Delivery Duration (minutes)
3. ⭐ Customer Rating (1-5 stars)

**Key Findings**:

| Variable Pair             | Correlation | Interpretation |
|---------------------------|-------------|----------------|
| Total Bill vs Delivery Time | -0.005      | 🚫 Almost no relationship |
| Total Bill vs Rating       | +0.0007     | 🚫 No meaningful connection |
| Delivery Time vs Rating    | -0.0016     | 🚫 Negligible correlation |

**Surprising Revelations**:
- 💸 Order value doesn't affect delivery speed
- ⏱️ Delivery duration doesn't impact ratings
- 🌟 Spending amount doesn't influence review scores



## 🔍 Key Findings

### 1️⃣ Chapter 1: The Big Picture 🌍
**❓ Business Question**: What are the overall key performance indicators and distributions of key metrics?


![image](https://github.com/user-attachments/assets/ebc03c93-3b39-4cc4-8f4d-437c8daafb13)


![image](https://github.com/user-attachments/assets/5d48044f-e17c-4e31-b991-1cf7c7746bb7)



**📊 KPIs**:
- 💰 **Total Revenue**: 4.24 Million SAR
- ⭐ **Average Rating**: 3.0/5 stars
- ⏱️ **Median Delivery Time**: 12.0 minutes

**💡 Insights**:
- 🏙️ Certain cities dominate order volume but not huge 
- 🕒 Delivery times show consistent patterns
- 💵 Most orders fall within typical price ranges

---

### 2️⃣ Chapter 2: When Do Customers Order? 🕒
**❓ Business Question**:  How do order patterns and revenue differ between morning (AM) and evening (PM) hours?

![image](https://github.com/user-attachments/assets/5f102e33-e77b-4c99-b6ea-ea08af8ae87c)

![image](https://github.com/user-attachments/assets/8c8b5c84-f882-4589-8790-a6a4f73a48ea)


**📊 Findings**:
- 🌙 PM accounts for 50.37% of orders (50.70% of revenue)
- 🌅 AM favorites: Vegetarian/Vegan & Fast Food
- 🌃 PM favorites: Indian & Italian Cuisine

---

### 3️⃣ Chapter 3: City Showdown 🏙️
**❓ Business Question**: How do cities compare in terms of revenue generation and customer satisfaction?

![image](https://github.com/user-attachments/assets/e9b0f796-567f-43f2-bb43-b6e9c35c3d48)



**🏆 Top Performers**:
1. Dammam
2. Buraidah
3. Mecca

**📌** All cities maintain ~3 star ratings consistently

---

### 4️⃣ Chapter 4: Restaurant Champions 🍽️
**❓ Business Question**: Which restaurant types are the most successful in terms of total revenue?

![image](https://github.com/user-attachments/assets/2427fc99-17a1-4620-8a32-2816e7bd2641)


**🥇 Top Revenue Generators**:
1. Vegetarian/Vegan
2. Indian Cuisine
3. Sushi

---

### 5️⃣ Chapter 5: Time Traveler ⏳
**❓ Business Question**:  What are the trends in total revenue over time (monthly)?

![image](https://github.com/user-attachments/assets/f0884cba-2a99-4a4d-91ad-ae779f5de7dd)


**📈 Peak Months**:
1. September 2023
2. August 2023
3. January 2024

**🔮** Overall upward trend with seasonal patterns


## 🎯 Conclusion & Key Takeaways

### 📌 Overall Findings
- 🚀 **Business Growth**: Consistent revenue growth (2022-2024) with clear seasonal peaks
- 🏙️ **Geographic Dominance**: Dammam, Buraidah, and Mecca emerge as top-performing cities
- 🕒 **Time Patterns**: Near-even AM/PM split (50.37% PM orders) with distinct cuisine preferences
- 🍽️ **Restaurant Stars**: Vegetarian/Vegan, Indian, and Sushi lead in revenue generation
- ⏱️ **Operational Insights**: Median 12-min delivery time with consistent 3-star ratings across cities

### 🔍 Surprising Discoveries
- ❓ **No Correlation Found** between:
  - 💸 Order value and delivery speed
  - ⏱️ Delivery time and customer ratings
  - 💵 Spending amount and review scores
- 🌟 Ratings remain stable (~3 stars) regardless of:
  - Location 🏙️
  - Order time 🕒
  - Restaurant type 🍽️

### 💡 Strategic Recommendations
1. **City Expansion**: Focus resources on top-performing cities (Dammam, Buraidah, Mecca)
2. **Time-Based Promotions**:
   - 🌅 AM: Boost Vegetarian/Vegan & Fast Food
   - 🌙 PM: Highlight Indian & Italian Cuisine
3. **Restaurant Partnerships**: Strengthen ties with top-performing categories
4. **Quality Consistency**: Maintain current delivery time standards (~12 mins median)
5. **Rating Improvement**: Investigate why ratings plateau at 3 stars despite other positive metrics

### 🔮 Future Research Directions
- 🧐 Deep dive into rating determinants beyond basic metrics
- 📅 Analyze weekday vs weekend patterns
- 🛒 Examine basket composition trends
- 🎯 Customer segmentation analysis


## ℹ️ [Dataset Reference ](https://www.kaggle.com/datasets/halaturkialotaibi/food-delivery)
