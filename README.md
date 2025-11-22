# 📊 Student Mental Health Dashboard — Power BI  
A data analytics project exploring mental health patterns among undergraduate students using the **University Student Mental Health Dataset (2021)**.  
This dashboard visualizes **stress, anxiety, depression, sleep, lifestyle factors, and risk levels** using advanced Power BI techniques and validated psychological scales.

---

## 📁 Dataset Description
This project uses the **University Student Mental Health 2021–10–10** dataset containing:

- **1192 students**
- **147 variables**
- Data collected through Qualtrics
- Includes demographics, lifestyle habits, exercise, sleep, social support, mindfulness, and multiple psychological scales

### 🎯 Psychological Scales Included
- **DASS-21** (Stress, Anxiety, Depression)
- **GAD-2** (Generalized Anxiety Disorder)
- **PHQ-2** (Depression screening)
- **PSS** (Perceived Stress Scale)
- **CATS** (Sleep attitude)
- **DERS-16** (Emotional regulation)
- **Mindfulness Scale (CAMS-R)**
- **Social Support Scale**

Scale scoring details referenced from **Lovibond & Lovibond (1995)** and dataset documentation.

---

## 📌 Project Objective
To design an **interactive Power BI dashboard** that helps educators and institutions:

- Understand student mental health patterns  
- Identify high-risk groups  
- Explore relationships between lifestyle, academics, and mental well-being  
- Support data-driven decision making for student support services  

---

## 📊 Dashboard Structure (4 Pages)

---

## 1️⃣ Overview Page
A high-level summary of student mental health.

### **KPIs Included**
- Total Students Surveyed  
- Average Stress, Anxiety & Depression (DASS-21)  
- Average Sleep Hours  
- % Well-Rested Students  
- Severity Distribution (Normal/Mild/Moderate/Severe)

### **Visualizations**
- KPI Cards  
- Donut Chart (Mental Health Status)  
- Line Chart (Pre vs Post COVID Anxiety/Stress)  
- Bar Chart (Average Stress by Province)  
- Slicers (Gender, Province, Age, Year of Study)

---

## 2️⃣ Stress, Anxiety & Depression Analysis
Deep dive into validated mental health indicators.

### **KPIs**
- % High Anxiety (GAD-2 ≥ 3)  
- % High Depression (PHQ-2 ≥ 3)  
- Average DASS-21 Stress, Anxiety, Depression  
- Average PSS Score

### **Visualizations**
- Severity distribution bar charts  
- Box plots comparing groups  
- Trend charts (Pre/Post COVID)  

---

## 3️⃣ Lifestyle & Academic Correlation
Understanding how habits influence mental well-being.

### **KPIs**
- Average Stress vs Sleep Hours  
- Average Stress vs Exercise Frequency  
- Mindfulness Scores vs Anxiety Levels  
- Sleep Adequacy vs Depression Risk  

### **Visualizations**
- Scatter Plot (Mindfulness vs Anxiety)  
- Column Charts (Sleep/Exercise vs Stress)  
- Heatmaps (Academic Year × Stress Levels)

---

## 4️⃣ Support, Risk & Recommendations
Identifying high-risk students and actionable insights.

### **KPIs**
- % Students Officially Diagnosed  
- % Wanting More Sleep  
- % Poor Rest  
- % High-Risk Students (clinical cutoffs)  
- Severity Breakdown (Normal → Extremely Severe)

### **Visualizations**
- KPI Cards  
- Donut/Stacked Column for severity  
- Matrix by Demographics  
- Recommendations Panel  

---

## 🧠 Key DAX Measures Used

```DAX
Total_Students = COUNTROWS('Table')

DASS_Stress =
([DASS_1] + [DASS_6] + [DASS_8] + [DASS_11] + [DASS_12] + [DASS_14] + [DASS_18]) * 2

DASS_Anxiety =
([DASS_2] + [DASS_4] + [DASS_7] + [DASS_9] + [DASS_15] + [DASS_19] + [DASS_20]) * 2

DASS_Depression =
([DASS_3] + [DASS_5] + [DASS_10] + [DASS_13] + [DASS_16] + [DASS_17] + [DASS_21]) * 2

Sleep_Hours =
SWITCH('Table'[Hours_sleep],
 1,4, 2,5, 3,6, 4,7, 5,8, 6,9, 7,10, 8,11, 9,12
)

High_Anxiety = IF('Table'[GAD_Total] >= 3, 1, 0)
