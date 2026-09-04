## OrthoIQ: Surgical Likelihood Analytics

An orthopedic healthcare analytics project exploring how patient characteristics can be used to estimate synthetic surgical likelihood and demonstrate an end-to-end healthcare machine-learning workflow.

## Project Overview

OrthoIQ was developed to combine orthopedic clinical domain knowledge with healthcare data analytics and machine learning.

The project begins with a synthetic general healthcare dataset and focuses on patients diagnosed with arthritis. Because the source dataset does not contain detailed orthopedic examination findings, imaging severity, conservative treatment history, or surgical outcomes, additional orthopedic variables and the surgical outcome were synthetically generated.

The purpose of OrthoIQ is not to create a clinically validated surgical decision tool. Instead, it demonstrates how a healthcare question can be translated into a structured analytics workflow involving data preparation, feature engineering, exploratory analysis, predictive modeling, model interpretation, threshold optimization, and patient stratification.

## Business / Clinical Question

**Can patient characteristics be used to estimate surgical likelihood within a simulated orthopedic arthritis population?**

The project also explores:

* Which model provides the strongest combination of predictive performance and interpretability?
* How does changing the classification threshold affect false negatives and false positives?
* Can predicted probabilities be translated into understandable patient-likelihood groups?

## Dataset

The project uses a synthetic general healthcare dataset containing **55,500 records**.

After removing exact duplicate records:

* **54,966 patient records remained**
* **9,218 arthritis records** were identified
* Arthritis represented approximately **16.8%** of the cleaned dataset

The original dataset does not contain sufficient orthopedic-specific clinical information or a surgical outcome.

Additional synthetic variables were therefore generated for the arthritis cohort, including:

* BMI
* Pain Score
* Functional Limitation
* Imaging Severity
* Conservative Treatment History
* Comorbidity Count
* Surgical Outcome

These variables are simulated and should not be interpreted as real patient observations.

## Analytical Workflow

The OrthoIQ workflow includes:

1. Data quality assessment and duplicate removal
2. Arthritis cohort identification
3. Synthetic orthopedic feature engineering
4. Clinical relationship simulation
5. Synthetic surgical-outcome generation
6. Exploratory data analysis and quality checks
7. Train/test splitting
8. Baseline classification
9. Logistic Regression modeling
10. Random Forest comparison
11. Model interpretation
12. ROC-AUC analysis
13. Classification-threshold analysis
14. Patient-level likelihood estimation
15. Likelihood stratification

## Model Features

The final classification models use:

* Age
* BMI
* Pain Score
* Functional Limitation
* Imaging Severity
* Conservative Treatment
* Comorbidity Count

The target variable is the synthetically generated binary surgical outcome.

## Model Performance

### Logistic Regression

Logistic Regression was selected as the preferred model.

| Metric            |    Result |
| ----------------- | --------: |
| Accuracy          | **85.8%** |
| Surgery Precision | **80.4%** |
| Surgery Recall    | **80.4%** |
| ROC-AUC           | **0.936** |

### Random Forest

| Metric         |    Result |
| -------------- | --------: |
| Accuracy       | **83.0%** |
| Surgery Recall | **76.1%** |
| ROC-AUC        | **0.913** |

Logistic Regression provided stronger overall performance while maintaining greater interpretability.

## Threshold Analysis

The default Logistic Regression classification threshold is 50%.

For an exploratory screening-oriented scenario, a **40% threshold** was also evaluated.

| Metric          | 50% Threshold | 40% Threshold |
| --------------- | ------------: | ------------: |
| Accuracy        |         85.8% |         85.1% |
| Surgery Recall  |         80.4% |     **86.6%** |
| False Negatives |           131 |        **90** |
| False Positives |           131 |           184 |

Lowering the threshold increased identification of synthetic surgery cases and reduced false negatives by **41 cases**, while producing only a small reduction in overall accuracy.

This illustrates how classification thresholds can be evaluated according to an analytical or operational objective rather than relying on accuracy alone.

The 40% threshold is exploratory and is **not a clinically validated cutoff**.

## Surgical Likelihood Stratification

Predicted probabilities were translated into three patient groups:

* **Lower Likelihood:** <40%
* **Elevated Likelihood:** 40–<70%
* **High Likelihood:** ≥70%

Observed synthetic surgery rates demonstrated clear separation:

| Likelihood Group | Observed Synthetic Surgery Rate |
| ---------------- | ------------------------------: |
| Lower            |                        **8.3%** |
| Elevated         |                       **52.0%** |
| High             |                       **89.0%** |

These categories demonstrate how continuous model predictions can be translated into more interpretable patient-stratification information.

## Key Takeaway

OrthoIQ demonstrates that model selection should consider more than predictive accuracy.

Logistic Regression outperformed Random Forest while also providing greater interpretability. Threshold analysis further demonstrated the tradeoff between identifying more potential positive cases and generating additional false-positive classifications.

Most importantly, the project demonstrates how orthopedic domain knowledge can be combined with data analytics to frame a clinical question, build an analytical workflow, evaluate model behavior, and communicate results in a healthcare context.

## Limitations

OrthoIQ is an educational and portfolio analytics project built using synthetic data.

The orthopedic variables and surgical outcome were synthetically generated using predefined clinical relationships. Model performance therefore represents the ability to recover patterns embedded within the simulation rather than evidence of real-world surgical predictive performance.

Actual orthopedic surgical decision-making includes additional factors such as diagnosis and joint involved, radiographic findings, symptom duration, prior procedures, medical contraindications, patient preferences, and surgeon judgment.

The model has not been externally validated on real orthopedic patients, and its predicted likelihoods, thresholds, and patient groups should not be interpreted as validated clinical risk estimates or decision criteria.

## Future Development

A future version of OrthoIQ could extend this framework using real orthopedic EHR and procedural data containing:

* Validated diagnoses
* Joint and procedure information
* Radiographic severity
* Detailed conservative treatment history
* Surgical procedures
* Patient-reported outcomes
* Postoperative outcomes

Future development would also require external validation, subgroup performance evaluation, probability calibration, and appropriate clinical governance before considering any real-world application.

## Tools & Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Logistic Regression
* Random Forest
* Google Colab
* Git / GitHub

## Repository Contents

`OrthoIQ_Surgical_Likelihood_Analytics.ipynb` — Complete analysis, feature engineering, machine-learning workflow, model evaluation, threshold analysis, and conclusions.

`README.md` — Project overview, methodology, results, limitations, and key findings.

## Disclaimer

This project is intended solely for educational and portfolio purposes. It is based on synthetic data and does not provide medical advice, determine surgical candidacy, or represent a validated clinical decision-support system.
