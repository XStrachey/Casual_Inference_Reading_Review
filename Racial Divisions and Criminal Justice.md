# Introduction

- This study provides **causal evidence** that **racial heterogeneity shapes punishment severity through electorate preferences and local discretion**, reinforcing the role of **ingroup bias in criminal justice policy**.
- This paper identifies a **non-monotonic, inverted U-shaped relationship** between **local punishment severity** and **Black population share** in a jurisdiction.

```mermaid
graph TD;
    subgraph Observed Nodes
        R[Racial Heterogeneity] -->|Influences| J[Jurisdiction];
        R -->|Electorate Preferences| P[Prosecutorial & Judicial Discretion];
        J -->|Causal Effect| S[Punishment Severity];
        P -->|Mediates| S;
        S -->|Determines| C[Charge Outcomes];
        J -->|Direct Effect| C;
        P -->|Direct Effect| C;
        X[Defendant Characteristics] -->|Controls in Model| C;
        X -->|Controls in Model| S;
        X -->|Controls in Model| J;
    end

    subgraph Unobserved Confounders
        U[Unobserved Factors] -.-> J;
        U -.-> S;
        U -.-> C;
    end
```

### **解释 DAG 关键结构**
#### **1. 主要因果路径**
- **\( J \) (Jurisdiction) → \( S \) (Punishment Severity) → \( C \) (Charge Outcomes)**  
  - **核心因果效应**：司法辖区的差异影响惩罚严厉程度，进而决定案件结果（如是否监禁）。
  
- **\( R \) (Racial Heterogeneity) → \( J \) (Jurisdiction) → \( S \) (Punishment Severity)**  
  - **选民偏好（Electorate Preferences）** 受种族异质性影响，进而影响地方法院的惩罚风格。

- **\( P \) (Prosecutorial & Judicial Discretion) → \( S \) (Punishment Severity) → \( C \) (Charge Outcomes)**  
  - **地方检察官 & 法官的自由裁量权** 影响惩罚政策，最终决定案件处理方式。

#### **2. 直接 & 间接影响**
- **\( J \) (Jurisdiction) → \( C \) (Charge Outcomes)**
  - 司法辖区可能 **独立于 \( S \) 影响案件处理**，如某些县的法官更倾向于判刑。

- **\( P \) (Prosecutorial & Judicial Discretion) → \( C \) (Charge Outcomes)**
  - 法律工作者在案件处理过程中有 **自由裁量权**，影响最终结果。

#### **3. 不可观测因素（\( U \)）**
- 可能的潜在混淆变量（**虚线连接**）：
  - **社会经济因素**（如贫困率、犯罪率）影响 **\( J \)**（司法辖区的风格）和 **\( C \)**（案件结果）。
  - **政策环境**（如历史上不同地区的惩罚文化）可能同时影响 **\( S \)** 和 **\( C \)**。

---

### **关键因果推断方法**
1. **固定效应模型（Fixed Effects Model）**
   - 通过控制 **被告特征 \( X \)**（种族、犯罪史）减少混淆因素的影响。
  
2. **多司法辖区被告（Multi-Jurisdiction Defendants）**
   - 研究 **同一被告在不同司法辖区的案件**，确保 **惩罚严厉程度是司法辖区的因果效应，而非被告自身特征导致的选择偏误**。

---

### **总结**
- 论文的核心因果路径：  
  **\( J \) (Jurisdiction) → \( S \) (Punishment Severity) → \( C \) (Charge Outcomes)，并受到 \( R \) (Racial Heterogeneity) 和 \( P \) (Prosecutorial & Judicial Discretion) 影响**。
- 研究通过：
  1. **控制可观测变量 \( X \) 以减少混淆**。
  2. **利用多辖区被告进行准实验分析，确保因果关系稳健**。
 
## Research Target Selection

### Harmonization Difficulties in Research Design

| **Challenge**              | **Description** |
|---------------------------|---------------|
| **Cross-Country Comparison Issues** | Lack of harmonized micro-level data and differences in crime definitions make cross-country comparisons unreliable. |
| **Within-U.S. Variation** | Even within the U.S., jurisdictions enforce laws differently, despite having the same state-level criminal code. |
| **Data Harmonization Across Jurisdictions** | Differences in data availability, crime categorization, and recording methods create inconsistencies across states. |
| **Solution: Focusing on Southern States** | By studying jurisdictions within the same state, the authors control for statutory differences and isolate discretionary enforcement variations. |

### **Comparison of This Study vs. Past Research: Inclusion of Arrest Charges**

| **Aspect**                     | **This Study (Feigenberg & Miller, 2021)** | **Past Research** |
|--------------------------------|---------------------------------|------------------|
| **Data Scope** | Includes **all arrest charges**, even if later dropped or downgraded. | Often limited to **convictions** or **incarceration cases only**. |
| **Charge Processing Coverage** | Tracks cases from **arrest → prosecution → sentencing**, capturing discretionary decisions by prosecutors. | Starts from **conviction stage**, missing prosecutor discretion and dropped charges. |
| **Potential Selection Bias** | Avoids bias by considering all charges, not just those leading to conviction. | **Selection bias**: Only analyzing convicted cases can distort estimates of sentencing disparities. |
| **Incarceration Decision Analysis** | Measures **whether a charge leads to incarceration**, not just sentence length. | Often examines **sentence severity (length)** rather than **whether incarceration occurs**. |
| **Impact on Punishment Severity Estimation** | Captures the **full decision-making process**, including **prosecutorial discretion** (charge reductions, plea deals). | Misses prosecutorial discretion, potentially **underestimating racial disparities**. |

# Data

## **1. Data Sources & Time Coverage**
| **State** | **Data Source** | **Time Period** | **Number of Jurisdictions (Counties)** |
|----------|-----------------|---------------|------------------|
| **Alabama** | Alabama Administrative Office of the Courts | 2000 – 2010 | 67 |
| **North Carolina** | North Carolina Administrative Office of the Courts | 2007 – 2014 | 100 |
| **Texas** | Texas Department of Public Safety | 2000 – 2010 | 253 |
| **Virginia** | Virginia Office of the Executive Secretary | 2006 – 2014 | 118 |

- **Four Southern states covered**: Alabama, North Carolina, Texas, and Virginia.
- **County-level data** covering **538 jurisdictions**.
- **Time span: 2000–2014**, with variations in availability across states.

---

## **2. Sample Size**
| **Category** | **Total Count** |
|-------------|---------------|
| **Total Defendants** | 7,000,000+ |
| **Total Cases** | 13,000,000+ |
| **Total Charges** | 16,000,000+ |
| **Average Charges per Defendant** | 2.3 - 3.1 |

- **Over 7 million defendants and 16 million charges**.
- **Each defendant is charged with an average of 2.3 - 3.1 offenses**.

---

## **3. Defendant Characteristics**
| **Variable** | **Description** |
|-------------|---------------|
| **Gender** | Majority male, ranging from **71.1% to 78.7%** of defendants. |
| **Race** | - Alabama & Virginia: Only **Black and White** included.<br>- North Carolina & Texas: **Black, White, and Hispanic**.<br>- **Race data missing for <1% of cases**. |
| **Age** | Adult defendants, **juvenile cases (under 16) excluded**. |
| **Criminal History** | Indicator for **prior convictions and prior incarceration history**. |

- **Race definitions differ by state**, but the key focus is on **Black vs. White disparities**.
- **Juvenile cases are excluded**, making this an adult defendant dataset.

---

## **4. Jurisdiction Characteristics**
| **Variable** | **Description** |
|-------------|---------------|
| **Black Share** | **Key independent variable**, measuring the proportion of Black residents in a jurisdiction. |
| **Economic Conditions** | Median income, poverty rate, and unemployment rate. |
| **Crime Rate** | Violent and property crime rates at the jurisdiction level. |
| **Political Preferences** | Voter preferences (Republican/Democrat support). |
| **Judicial Resources** | Court budgets, availability of **public defenders**, and judicial staffing. |

- **Black share is the primary explanatory variable**, driving the study’s causal analysis.
- **Crime rate and economic factors included as controls** to isolate racial heterogeneity effects.

---

## **5. Charge Types**
| **Charge Type** | **Description** | **Approximate Share** |
|---------------|----------------|--------------------|
| **Violent Crimes** | Assault, robbery, homicide, etc. | 20-25% |
| **Property Crimes** | Burglary, larceny, fraud. | 30-35% |
| **Drug Offenses** | Drug possession, distribution. | 15-20% |
| **Crimes Against Society** | DUI, weapons possession, disorderly conduct. | 10-15% |
| **Other Offenses** | Misdemeanors, infractions. | <10% |

- **Property and violent crimes account for the largest share** of cases.
- **Drug offenses represent 15-20%**, varying by state.
- **Crimes against society include DUI and firearm-related offenses**.

---

## **6. Measures of Punishment Severity**
| **Measure** | **Definition** | **Purpose** |
|------------|-------------|-----------|
| **Confinement Rate** | Probability of a defendant receiving **incarceration**. | **Primary measure** of punishment severity. |
| **Conviction Rate** | Probability of a defendant being **found guilty**. | Used as an alternative indicator of severity. |
| **Sentence Length** | Length of incarceration for convicted offenders. | Captures the **depth of punishment**. |
| **Plea Bargain Rate** | Proportion of cases resolved via plea agreements. | Reflects prosecutorial strategy differences. |

- **Confinement Rate is the primary measure**, as incarceration represents the harshest form of punishment.
- **Conviction Rate and Sentence Length serve as robustness checks**.
- **Plea bargaining rates vary across jurisdictions**, influencing punishment severity.

---

## **7. Excluded Data (Sample Restrictions)**
| **Exclusion Criteria** | **Reason for Exclusion** |
|------------------------|------------------------|
| **Non-DWI Traffic Offenses** | Minor traffic infractions (e.g., speeding tickets) are not part of the criminal justice system in the same way as other charges. |
| **Juvenile Cases (Defendants under 16)** | The study focuses on adult defendants, and juvenile justice systems follow different legal frameworks. |
| **Technical Probation/Parole Violations** | These violations often result from administrative issues rather than new criminal behavior. |
| **Cases Transferred to Circuit/Superior Courts** | Some cases are handled at a higher court level and may not follow the same sentencing patterns as county-level courts. |
| **Cases with Missing Race Information** | To maintain data consistency, cases where the defendant’s race was not recorded (less than 1%) were excluded. |
| **Dismissed or Withdrawn Cases (in Some Robustness Checks)** | In some alternative specifications, the authors exclude cases where charges were dropped, as they do not result in sentencing outcomes. |

---

## **8. Race Data Restrictions by State**

| **State** | **Race Categories Available** | **Restrictions Applied** | **Reason for Exclusion/Adjustment** |
|----------|----------------------------|------------------------|--------------------------------|
| **Alabama** | Black, White | Cases missing race data are excluded. | Only two race categories recorded in the dataset. |
| **North Carolina** | Black, White, Hispanic | Cases missing race data are excluded.<br>Hispanic defendants are included in robustness checks but not in the main analysis. | Race data is more comprehensive, but the focus is on Black vs. White disparities. |
| **Texas** | Black, White, Hispanic | Hispanic defendants are excluded from main analysis.<br>Cases missing race data are excluded. | To maintain consistency with Alabama & Virginia, Hispanic cases are excluded in the primary specification. |
| **Virginia** | Black, White | Cases missing race data are excluded. | Only Black and White categories are available. |

---
