

\# ML-Based Adaptive PI Gain Tuning Framework



\## 📌 Overview



Traditional PI tuning methods (Ziegler–Nichols, manual tuning, or brute-force search) are often computationally expensive and struggle to scale when plant parameters vary dynamically.



This project proposes a \*\*supervised regression approach\*\* to predict optimal Proportional () and Integral () gains directly from plant dynamics, replacing iterative tuning with real-time inference.



---



\## 🎯 Objective



Given a second-order plant defined as:



The framework predicts the optimal:



\* \*\*Proportional gain\*\* ()

\* \*\*Integral gain\*\* ()



---



\## 🧠 Mathematical Foundation



The plant denominator  is mapped to the standard second-order form:



Where the natural frequency () and damping ratio () are:



\* 

\* 



\### Optimization Objective



To determine the "True Optimal" gains for the training set, we minimize the cost function :



\*\*Metrics included:\*\*



\* : Settling Time

\* : Percentage Overshoot

\* : Integral of Squared Error



---



\## ⚙️ Methodology



\### 1. Dataset Generation



\* Generated ~200 unique second-order plants by varying .

\* Performed a grid-search optimization to find the  pair that minimizes  for each plant.

\* \*\*Result:\*\* A supervised dataset mapping .



\### 2. ML Models Evaluated



The following regressors were benchmarked to find the best mapping:



\* \*\*Random Forest Regressor\*\* (Ensemble)

\* \*\*Neural Network\*\* (MLPRegressor)

\* \*\*XGBoost Regressor\*\* (Gradient Boosting)



---



\## 📊 Results



The \*\*XGBoost Regressor\*\* emerged as the top performer, achieving an  score between \*\*0.86 – 0.92\*\*.



\### Closed-loop Validation (Unseen Plant)



| Metric | True Optimal | ML Predicted |

| --- | --- | --- |

| \*\*Settling Time\*\* | 3.07 s | 2.32 s |

| \*\*Overshoot\*\* | 0% | 0.7% |

| \*\*ISE\*\* | 0.749 | 0.741 |



> \*\*Note:\*\* The ML-predicted controller achieved comparable (and in some cases, faster) performance with negligible overshoot compared to the computationally expensive brute-force method.



---



\## 🚀 Key Contributions



\* \*\*Hybrid Approach:\*\* Seamlessly integrates Control Theory with Machine Learning.

\* \*\*Automation:\*\* Built a full pipeline from plant generation to model validation.

\* \*\*Efficiency:\*\* Reduced gain-tuning time from minutes (optimization-based) to milliseconds (inference-based).



---



\## 🛠 Tech Stack



\* \*\*Scientific Computing:\*\* `NumPy`, `SciPy`

\* \*\*Control Systems:\*\* `python-control`

\* \*\*Machine Learning:\*\* `scikit-learn`, `XGBoost`

\* \*\*Visualization:\*\* `Matplotlib`, `Seaborn`



---



\## 🔮 Future Work



\* \[ ] Implement \*\*Bayesian Optimization\*\* for faster hyperparameter tuning.

\* \[ ] Extend the framework to \*\*Full PID Tuning\*\* ( included).

\* \[ ] Introduce \*\*Disturbance \& Noise\*\* modeling for robustness testing.

\* \[ ] Explore \*\*Reinforcement Learning (RL)\*\* for real-time adaptive control in non-linear environments.



---



\*\*Author:\*\* \[Vansh Dev](https://github.com/vanshdev27)



\*Data Science \& Control Systems Enthusiast\*



---


