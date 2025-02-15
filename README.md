**Crime Data Analysis Report**

## **1. Data Overview**

### **Dataset Summary**
The dataset consists of 20,000 records and 22 columns, containing information about crime occurrences, locations, victim demographics, and crime categories.

**Key Columns:**
- **Geographical Data**: Latitude, Longitude, Location
- **Time Data**: Date_Reported, Date_Occurred, Time_Occurred
- **Crime Details**: Area_ID, Area_Name, Crime_Category
- **Victim Information**: Victim_Age, Victim_Sex, Victim_Descent
- **Crime Execution**: Weapon_Used_Code, Weapon_Description, Modus_Operandi

### **Observations**
- **Geographical Distribution:** Latitude (0 - 34.3281), Longitude (-118.6634 to 0). Outliers need cleaning.
- **Time of Occurrence:** Most crimes occur in the afternoon (~1352.38 mean time).
- **Victim Age:** Ranges from -2 to 99 (erroneous entries to be handled). Median age: 31.
- **Crime Type (Part 1-2):** Mean value of 1.4181 suggests slightly more Part 1 crimes.
- **Spatial Distribution:** Crimes are evenly spread across different areas.
- **Victim Demographics:** Younger individuals are more frequent victims.
- **Premise and Weapon Usage:** Certain premises and weapons are associated with specific crimes.

---

## **2. Model Performance Comparison**

### **XGBoost Model**
- **Accuracy:** 0.96
- **Best Precision & Recall for:** "Property Crimes" (0.99)
- **Weakest Performance for:** "Other Crimes" (Precision: 0.42, Recall: 0.23)
- **Weighted Averages:** Precision: 0.95, Recall: 0.96, F1-Score: 0.96

**Observations:**
- Best performing model overall with the highest accuracy.
- Struggles with "Other Crimes" due to low recall.

---

### **Random Forest Model**
- **Accuracy:** 0.94
- **Best Precision for:** "Other Crimes" (1.00), but recall is poor (0.03)
- **Weakest Performance for:** "Crimes against Persons" (Precision: 0.73)
- **Weighted Averages:** Precision: 0.94, Recall: 0.94, F1-Score: 0.93

**Observations:**
- Performs well for most categories but struggles with "Other Crimes."
- High precision for "Other Crimes" but extremely low recall suggests misclassification.

---

### **SVM Model**
- **Accuracy:** 0.93
- **Best Precision for:** "Fraud and White-Collar Crimes" (0.98)
- **Weakest Performance for:** "Crimes against Persons" (Precision: 0.38)
- **Weighted Averages:** Precision: 0.93, Recall: 0.93, F1-Score: 0.93

**Observations:**
- Good overall accuracy but weak in classifying "Other Crimes."
- Strongest in "Fraud and White-Collar Crimes."

---

### **Decision Tree Model**
- **Accuracy:** 0.93
- **Best Precision & Recall for:** "Property Crimes" (0.98)
- **Weakest Performance for:** "Other Crimes" (Precision: 0.40, Recall: 0.29)
- **Weighted Averages:** Precision: 0.93, Recall: 0.93, F1-Score: 0.93

**Observations:**
- Comparable to the SVM model with similar strengths and weaknesses.
- Performs well for "Property Crimes" but struggles with "Other Crimes."

---

## **3. Summary & Recommendations**

### **Best Model: XGBoost**
- **Highest accuracy (0.96) and best overall performance.**
- Needs improvement in detecting "Other Crimes" due to poor recall.

### **Key Findings & Improvements:**
1. **Handling Outliers**: The latitude/longitude values containing zeros and victim age values below zero must be cleaned.
2. **Feature Engineering**: Additional features like time-based crime patterns could help improve classification.
3. **Balancing "Other Crimes" Data**: Models struggle to classify this category, indicating possible data imbalance.
4. **Hyperparameter Tuning**: Further refinement of model parameters might enhance performance.
5. **Alternative Models**: Exploring deep learning techniques or ensemble models may boost results further.

### **Final Recommendation:**
- **Use XGBoost** for final predictions.
- **Improve "Other Crimes" classification** through feature engineering and data augmentation.
- **Implement more data preprocessing** to remove outliers and incorrect values.


