ML-Based Adaptive PI Gain Tuning Framework

📌 Overview



This project presents a data-driven PI controller tuning framework that integrates control theory, numerical optimization, and machine learning.



Traditional PI tuning methods (e.g., Ziegler–Nichols, manual tuning, brute-force search) are computationally expensive and difficult to scale across dynamically varying plant parameters.



This project proposes a supervised regression approach to predict optimal PI gains directly from plant dynamics.



🎯 Objective



Given a second-order plant:



𝐺

(

𝑠

)

=

1

𝑠

2

\+

𝑎

𝑠

\+

𝑏

G(s)=

s

2

+as+b

1

&nbsp;	​





Predict optimal:



Proportional gain 

𝐾

𝑝

K

p

&nbsp;	​





Integral gain 

𝐾

𝑖

K

i

&nbsp;	​





Using machine learning instead of repeated brute-force tuning.



🧠 Mathematical Foundation



The plant denominator:



𝑠

2

\+

𝑎

𝑠

\+

𝑏

s

2

+as+b



is compared to standard second-order form:



𝑠

2

\+

2

𝜁

𝜔

𝑛

𝑠

\+

𝜔

𝑛

2

s

2

+2ζω

n

&nbsp;	​



s+ω

n

2

&nbsp;	​





Where:



𝜔

𝑛

=

𝑏

ω

n

&nbsp;	​



=

b

&nbsp;	​





𝜁

=

𝑎

2

𝑏

ζ=

2

b

&nbsp;	​



a

&nbsp;	​





Classical control performance indices were incorporated:



Settling Time (Ts)



Overshoot (OS)



Integral of Squared Error (ISE)



Optimization objective:



𝐽

(

𝐾

𝑝

,

𝐾

𝑖

)

=

0.5

𝑇

𝑠

\+

5

𝑂

𝑆

\+

0.01

𝐼

𝑆

𝐸

J(K

p

&nbsp;	​



,K

i

&nbsp;	​



)=0.5T

s

&nbsp;	​



+5OS+0.01ISE

⚙️ Methodology

1️⃣ Dataset Generation



Generated ~200 second-order plants



Performed grid-search gain optimization for each plant



Created supervised dataset:



(

𝑎

,

𝑏

)

→

(

𝐾

𝑝

,

𝐾

𝑖

)

(a,b)→(K

p

&nbsp;	​



,K

i

&nbsp;	​



)

2️⃣ Machine Learning Models Evaluated



Random Forest Regressor



Neural Network (MLPRegressor)



XGBoost Regressor



📊 Results



Best performing model: XGBoost



R² ≈ 0.86–0.92 (depending on cost formulation)



Low MAE



Stable predictions across unseen plants



Closed-loop Validation



For unseen plant:



Metric	True Optimal	ML Predicted

Settling Time	3.07 s	2.32 s

Overshoot	0%	0.7%

ISE	0.749	0.741



The ML-predicted controller achieved comparable or improved integrated error performance with minimal overshoot.



📈 Model Diagnostics



Residual analysis shows unbiased prediction



Feature importance indicates plant stiffness parameter (b) significantly influences gain tuning



Ensemble models outperform physically transformed feature sets



🚀 Key Contributions



Integrated control theory and ML regression



Automated dataset generation pipeline



Multi-model comparison framework



Closed-loop validation on unseen plants



Realistic performance cost formulation



🔮 Future Work



Hyperparameter tuning via Bayesian Optimization



Extend framework to full PID tuning



Incorporate disturbance/noise modeling



Explore reinforcement learning-based adaptive control



🛠 Tech Stack



Python



NumPy



SciPy



python-control



scikit-learn



XGBoost



Matplotlib



👤 Author



Vansh Dev

Data Science \& Control Systems Enthusiast

"# ML-Based-Adaptive-PI-Gain-Tuning-Framework" 
