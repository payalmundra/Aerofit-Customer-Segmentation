# Aerofit Market Segmentation: Optimizing Sales Strategy via Predictive Modeling

> *Python | Random Forest | Kruskal-Wallis Test | Probability Analysis*

---

##  Project Overview
An end-to-end data science project focused on customer segmentation and predictive modeling using demographic and behavioral data. The goal was to optimize Aerofit's sales strategy by moving from intuition-based selling to data-driven targeting.

This workflow combines **Descriptive Statistics (Probability)**, **Machine Learning**, and **Robust Hypothesis Testing** to ensure model outputs reflect real customer patterns.

---

## Dataset
* **Records:** 180 customer observations
* **Features Processed:** 9
* **Key Variables:** Income, Age, Usage Frequency, Education, Gender, Fitness Level

---

## Statistical Inference & Customer Profiling
*Before building predictive models, I performed a rigorous statistical analysis to build "Initial Customer Personas."*

### 1. Conditional Probability Analysis
I calculated the marginal and conditional probabilities to understand the "raw signal" in the data.
* **P(KP781 | Fitness = 5):** **93.5%**. (If a customer rates their fitness as 5/5, they are almost guaranteed to buy the Premium model).
* **P(KP781 | Income > $70k):** **100%**. (Income is a hard threshold for the premium segment).
* **P(KP281 | Age < 30):** High probability, indicating the entry-level treadmill appeals to younger demographics.

### 2. Derived Customer Personas (Hypothesis)
Based on the data, I identified three potential target profiles:

| Profile | Product | Demographics | Behavior |
| :--- | :--- | :--- | :--- |
| **The Starter** | **KP281** | Age 20-30, Income $30k-$50k | Moderate usage (2-3x/week), Avg Fitness |
| **The Upgrader** | **KP481** | Age 25-35, Income $40k-$60k | Consistent usage (3-4x/week), Mid-level Fitness |
| **The Pro** | **KP781** | Age 25-40, Income $70k+ | High usage (5x+/week), High Fitness |

> **Critical Observation:** The profiles for **KP281** and **KP481** showed significant overlap in Income and Usage, leading to the hypothesis that they might be the same customer segment.

---

##  Workflow & Key Results

### 1️⃣ Phase 1: Predictive Modeling (The Test)
* **Goal:** Test if a Machine Learning model (Random Forest) could accurately distinguish between the three personas defined above.
* **Result:** **64% Accuracy**.
* **Failure Analysis:** The model performed perfectly on the **Premium (KP781)** segment but consistently confused the **Entry (KP281)** and **Mid-tier (KP481)** customers.

### 2️⃣ Statistical Validation (The Diagnosis)
To confirm if the overlap between KP281 and KP481 was real or a model error, I performed rigorous hypothesis testing on **Income** (the primary feature).

* **A. Assumption Checking:**
    * **Normality (Shapiro-Wilk):** Failed ($p < 0.05$). The data is not normally distributed.
    * **Homogeneity of Variance (Levene’s Test):** Failed ($p < 0.05$). The Premium group has significantly different variance.

* **B. Robust Testing (The Pivot):**
    * Since assumptions for ANOVA were violated, I switched to **Non-Parametric Tests**:
    * **Kruskal-Wallis H Test:** Confirmed significant differences exist overall ($p < 0.05$).
    * **Mann-Whitney U Test (Post-Hoc):**
        * *KP281 vs KP481:* **No significant difference** ($p > 0.05$). The overlap is mathematically proven.
        * *KP781 vs Others:* **Significant difference**.

### 3️⃣ Phase 2: Strategic Pivot (The Solution)
Reframed the problem from "Product Prediction" to "Value Segmentation" based on the statistical proof:
* **Mass Market Segment:** KP281 + KP481
* **Premium Segment:** KP781

### 4️⃣ Final Model Performance
* **Accuracy:** **94.44%**
* **Mass Market Recall:** 100%
* **Premium Precision:** 100%

---

## Business Recommendations
1.  **Consolidate Marketing:** Stop running separate ad campaigns for KP281 and KP481. Their profiles are identical. Run a single "General Fitness" campaign to maximize ROI.
2.  **Usage-Based Upselling:** Since demographics cannot predict the choice between the $1,500 and $1,750 models, sales staff should use **consultative selling** (asking about weekly usage) to upsell to the KP481.
3.  **Premium Exclusivity:** Target the **Premium (KP781)** segment exclusively on high-income channels (LinkedIn) and fitness communities (Strava), as they are statistically distinct from the general population.

---

## Tools & Technologies
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Machine Learning:** Scikit-Learn (Random Forest)
* **Statistics:** SciPy (Shapiro-Wilk, Levene, Kruskal-Wallis, Mann-Whitney U)
* **Visualization:** Matplotlib, Seaborn

---

## How to Run

1. Clone the repository:  
```bash
git clone [(https://github.com/payalmundra/Aerofit-Customer-Segmentation)]
