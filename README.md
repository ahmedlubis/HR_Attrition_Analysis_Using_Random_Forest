# 👥 HR Employee Attrition Analysis using Random Forest

## 📖 Dataset Overview

The analysis uses the **HR Employee Attrition** dataset, which originally contained **14,999 observations** and **10 variables**.

To ensure data quality and model stability, all rows containing missing values were removed using `drop_na()`, resulting in a cleaned dataset of **14,430 observations**.

### Dataset Features

| Variable | Description |
|----------|-------------|
| **left** | **Target variable** indicating employee status: **Stayed (0)** or **Left (1)** |
| **satisfaction_level** | Employee job satisfaction score |
| **last_evaluation** | Latest employee performance evaluation score |
| **number_project** | Total number of projects handled by the employee |
| **average_montly_hours** | Average monthly working hours |
| **time_spend_company** | Number of years the employee has worked at the company |
| **work_accident** | Whether the employee experienced a workplace accident |
| **promotion_last_5years** | Whether the employee received a promotion within the last five years |
| **department** | Employee's department or business unit |
| **salary** | Employee salary category (**Low**, **Medium**, or **High**) |

---

# 🌲 Random Forest Model

A **Random Forest classifier** was trained to predict employee attrition using:

- **500 Decision Trees**
- **70% Stratified Training Set** (**10,102 observations**)
- **30% Testing Set** (**4,328 observations**)

The model leverages ensemble learning to improve predictive performance while reducing overfitting.

---

# 📊 Model Performance

The Random Forest model achieved excellent predictive performance on unseen data.

| Metric | Result |
|---------|--------|
| **Out-of-Bag (OOB) Error Rate** | **1.00%** |
| **Testing Accuracy** | **98.75%** |
| **No Information Rate (Baseline)** | **79.21%** |
| **Sensitivity (Stayed)** | **99.82%** |
| **Specificity (Left)** | **94.67%** |

### Performance Interpretation

### ✅ Overall Accuracy

The model achieved an impressive **98.75% accuracy** on the testing dataset, substantially outperforming the baseline **No Information Rate (79.21%)**.

This demonstrates that the Random Forest model is highly effective at distinguishing employees who are likely to stay from those who are likely to leave.

### ✅ Out-of-Bag Validation

The **Out-of-Bag (OOB) Error Rate** is only **1%**, indicating excellent internal validation performance and strong model generalization without significant overfitting.

### ✅ Sensitivity

The model correctly identifies employees who **remain with the company** in **99.82%** of cases.

This extremely high recall minimizes false predictions that loyal employees will resign.

### ✅ Specificity

The model correctly detects employees who actually **leave the company** in **94.67%** of cases.

This indicates strong capability in identifying potential employee attrition before it occurs.

---

# 📈 Feature Importance

The Random Forest algorithm evaluates feature importance using two metrics:

- **Mean Decrease Accuracy (MDA)** – Measures how much prediction accuracy decreases when a feature is removed.
- **Mean Decrease Gini (MDG)** – Measures how effectively a variable improves decision tree splits.

---

## 🥇 Primary Driver of Employee Attrition

### **Job Satisfaction (`satisfaction_level`)**

Job satisfaction is by far the most influential predictor of employee turnover.

| Metric | Value |
|---------|------:|
| Mean Decrease Accuracy | **215.97** |
| Mean Decrease Gini | **1124.48** |

### Interpretation

Employees with lower satisfaction levels are significantly more likely to resign, making satisfaction the strongest determinant of employee retention.

---

## 🥈 Secondary Drivers

Several operational and workload-related variables also contribute substantially to predicting employee attrition.

| Feature | Mean Decrease Gini |
|---------|-------------------:|
| **time_spend_company** | **593.85** |
| **number_project** | **581.12** |
| **average_montly_hours** | **484.80** |
| **last_evaluation** | **419.98** |

### Interpretation

These findings indicate that employee turnover is strongly associated with:

- Workload intensity
- Number of assigned projects
- Working hours
- Employee tenure
- Performance evaluation

Together, these variables suggest that operational demands and organizational experience play an important role in influencing resignation decisions.

---

## 📉 Low-Impact Features

The following variables contribute relatively little to the predictive performance of the model:

- **Work_accident**
- **promotion_last_5years**
- **department**
- **salary**

### Interpretation

Although these variables may influence employee experiences, they provide limited predictive value compared with employee satisfaction and workload-related factors.

The Random Forest model indicates that **daily work experience** has a much stronger relationship with employee attrition than structural or demographic characteristics.

---

# 📝 Key Findings

The analysis highlights several important insights:

- **Job satisfaction** is the strongest predictor of employee attrition.
- Employees with heavier workloads, longer working hours, and extended company tenure are more likely to leave.
- The Random Forest model achieves **98.75% testing accuracy** with only a **1% Out-of-Bag error**, demonstrating excellent predictive capability.
- Satisfaction and workload variables contribute far more to turnover prediction than salary, department, workplace accidents, or recent promotions.

Overall, the results suggest that improving employee satisfaction and effectively managing workload are likely to have a greater impact on employee retention than structural organizational factors alone.
