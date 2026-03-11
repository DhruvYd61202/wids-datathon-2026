# wids-datathon-2026
Predicting time-to-threat for wildfire evacuation zones using right-censored survival analysis for the WiDS Global Datathon 2026.
# WiDS Global Datathon 2026: Wildfire Survival Analysis

## 📌 Overview
This repository contains our team's code and ML pipelines for the **WiDS Global Datathon 2026**. The challenge involves predicting the probability that a wildfire will threaten an evacuation zone within **12, 24, 48, and 72 hours**, using data from only the first five hours after ignition [1]. 

We are tackling this as a **right-censored survival analysis** problem to provide emergency responders with both urgency rankings and calibrated risk estimates [2, 3]. The real-world early-incident wildfire data is provided by Watch Duty [4].

## 👥 The Team
We are an all-student team of 3 collaborating to build end-to-end ML pipelines and officially competing for the **$2,500 Student Team Prize** [5, 6].

## 🎯 Evaluation Metrics
Our models are optimized for the competition's specific **Hybrid Score**, which is calculated as follows [7]:
**Hybrid Score = 0.3 x C-index + 0.7 x (1 - Weighted Brier Score)**

*   **C-index (30%):** Evaluates how well the model ranks fires by urgency [7].
*   **Weighted Brier Score (70%):** Evaluates the calibration of our probabilities at the 24h, 48h, and 72h horizons, with the heaviest weight placed on the 48-hour mark [7, 8].

## 🛠️ Tech Stack & MLOps Practices
To ensure reproducibility and adhere to professional software engineering principles, our workflow utilizes:
*   **Deep Learning Framework:** PyTorch [9].
*   **Version Control:** Git & GitHub (Branching, PRs, and Code Reviews) [10].
*   **Data Versioning:** DVC (Data Version Control) to track large datasets outside of Git [11].
*   **Experiment Tracking:** MLflow to systematically log parameters, metrics (C-index, Brier Score), and model versions [12, 13].

## ⚙️ Submission Requirements & Constraints
Our final inference pipeline is designed to meet Kaggle's strict code requirements [4, 14, 15]:
*   Execution within a Kaggle Notebook (<= 4 hours run-time) [15].
*   Internet access disabled during inference [15].
*   Strict output schema: `event_id`, `prob_12h`, `prob_24h`, `prob_48h`, `prob_72h` [4].
*   Row-wise monotonicity enforced (`prob_12h <= prob_24h <= prob_48h <= prob_72h`) with probabilities strictly between [16] [4].

## 🚀 How to Collaborate (Team Workflow)
1. **Never commit directly to `main`.** Create a new branch for your feature or experiment.
2. Track any dataset changes using **DVC** [11].
3. Log all model runs and hyperparameters to our central **MLflow** dashboard [13].
4. Submit a Pull Request (PR) for code review before merging into the main branch [10].
