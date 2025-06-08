# A Tale from India: The Country Mouse and the City Mouse - Where is Well-being in Modern Society? 

## Project Overview

이 프로젝트는 고전 이솝우화 '시골쥐 도시쥐'의 메세지를 현대 사회의 데이터로 검증하고자 했습니다.
도시의 풍요로움 뒤에 숨겨진 스트레스와 위험이 시골의 소박한 평화보다 과연 더 나쁜지, 캐글의 Exploring Mental Health Data를 통해 분석해 보았습니다.

This project delves into the timeless wisdom of Aesop's fable, "The Country Mouse and the City Mouse," by examining whether its core message about the hidden stresses of urban life versus the simple peace of rural living still holds true in modern society. I utilize a mental health dataset from India to investigate the well-being of urban versus rural inhabitants.

## Motivation

이 프로젝트는 고전 우화를 현대의 정신 건강 데이터와 연결하여 데이터 분석을 통해 독창적인 탐구를 시도한 것입니다. 
목표는 서로 다른 환경에서의 인간의 웰빙에 대해 겉보기에는 단순하지만 실은 깊은 의미를 가진 질문을 데이터로 풀어보는 것이었습니다. 

This project was initiated as a unique exploration into data analysis, connecting a classical fable with contemporary mental health data. The aim was to use data to address a seemingly simple, yet profound, question about human well-being in different environments.

## Dataset

* **Name:** Exploring Mental Health Data
* **Source:** [https://www.kaggle.com/competitions/playground-series-s4e11/overview]
* **Key Features:** The dataset comprises survey responses related to various aspects of life in India. We meticulously preprocessed and categorized the original columns to analyze their impact on mental health within urban and rural contexts.

    **Original Columns:**
    * `id`
    * `Gender`
    * `Age`
    * `City`
    * `Working Professional or Student`
    * `Profession`
    * `Academic Pressure`
    * `Work Pressure`
    * `CGPA`
    * `Study Satisfaction`
    * `Job Satisfaction`
    * `Sleep Duration`
    * `Dietary Habits`
    * `Degree`
    * `Have you ever had suicidal thoughts ?`
    * `Work/Study Hours`
    * `Financial Stress`
    * `Family History of Mental Illness`
    * `Depression`

    **Categorization for Analysis:**
    * **Lifestyle Indicators:** `Sleep Duration`, `Dietary Habits`, `Work/Study Hours`
    * **Stress Indicators:** `Academic Pressure`, `Work Pressure`, `Financial Stress`
    * **Mental Health Indicators:** `Depression`, `Have you ever had suicidal thoughts ?` (and `Family History of Mental Illness` as a background factor for mental health)
    * **Demographic/Contextual:** `Age`, `Profession`, `Degree`, ``City` (used for Urban/Rural classification)`

* **Urban/Rural Definition:** Based on per capita GRP (Gross Regional Product) data from India's Ministry of Statistics and Program Implementation and public data portals, the top 7 states/cities were categorized as 'Urban,' and the bottom 5 as 'Rural.'
* **Sample Size:** Urban (26,808 samples) and Rural (25,072 samples). All comparisons were made by analyzing 100% ratios for both populations to account for sample size differences.

## Key Questions & Hypotheses

1. 큰 도시와 작은 도시(시골)간에 라이프스타일 및 정신건강 지표에서 유의미한 차이가 있을까?
2. 어떤 요인이 특정 지역(도시/시골)에서 정신겅강과 더 관계가 있을까?
   
1.  **Are there statistically significant differences in lifestyle and mental health indicators between residents of large cities and smaller towns/rural areas in India?**
2.  **Which factors have a more substantial impact on mental health in either urban or rural settings?**

**Specific Hypotheses:**

* '도시쥐' 가설 : 도시 거주자는 스트레스가 높고 정신건강 지표가 나쁜 것이다.
* '시골쥐' 가설 : 시골 거주자는 건강한 라이프스타일과 긍정적인 정신건강 지표를 보일 것이다.
  
* **"City Mouse" Hypothesis:** Urban dwellers are expected to experience higher stress levels and poorer mental health indicators compared to their rural counterparts.
* **"Country Mouse" Hypothesis:** Rural dwellers are expected to exhibit healthier lifestyle patterns and more positive mental health indicators.

## Analysis Methodology

* 데이터 전처리: 범주형 변환, 샘플 불균형을 고려한 비율비교
* 통계적 검정:
    * 카이제곱검정: 도시와 시골 간 각 특성(연령, 직업, 학위, 수면시간, 스트레스 등) 유의미한 차이 확인
    * 스피어만 상관계수: 정신건강 지표와 라이프스타일/스트레스 지표 간의 상관관계 분석
* 머신러닝 모델:
    * 우울증 판편을 위한 이진 분류 모델 구축 (Logistic Regression, RandomForest, XGBoost, LightGBM)
    * 모델의 특성 중요도(Feature Importance)를 활용하여 정신건강에 영향을 미치는 주요 요인 식별
      
* **Data Preprocessing:** Categorical variable transformation for statistical tests (e.g., converting relevant numerical features to categorical bins).
* **Statistical Testing:**
    * **Chi-squared Test:** Used to determine statistically significant differences in the distribution of various characteristics (age, profession, education, sleep habits, diet, stress indicators, mental health indicators) between urban and rural populations.
    * **Spearman Correlation Coefficient:** Applied to analyze the correlation between mental health indicators and lifestyle/stress factors after one-hot encoding categorical variables.
* **Machine Learning Models:**
    * Developed binary classification models (Logistic Regression, RandomForest, XGBoost, LightGBM) to predict depression likelihood.
    * Utilized **Feature Importance** from these models to identify key factors significantly influencing mental health. Models achieved over 93% accuracy on the test set.

## Key Findings

* 인구통계: 도시와 농촌 지역 간에는 연령, 직업, 교육 수준 분포에서 뚜렷한 차이가 나타났습니다. 도시 지역은 18~25세의 청년층과 학생 비율이 높았던 반면, 시골 지역은 교육 관련 직종 종사자와 대학원 학위 소지자 비율이 높았습니다. 이는 고등교육 후 농촌으로의 회귀 현상을 시사합니다.
* 라이프스타일: 예상과 달리 도시 거주자의 라이프스타일 지표(식습관등)가 시골보다 약간 더 좋게 나왔습니다. 이는 시골 지역의 도시화 진행이 영향을 미쳤을 수 있습니다.
* 스트레스 지표: 도시 거주자들은 시골 거주자에 비해 업무 성과 압박과 경제적 부담 수준이 유의미하게 높습니다.
* 정신 건강 지표: 통계적으로 유의미한 차이가 있었으며, 시골 거주자의 정신건강 지표가 도시보다 상대적으로 긍정적이었습니다.
* 상관관계 분석: 현재 데이터셋 기준으로는 생활 방식/스트레스 지표와 정신 건강 지표 간에 강한 직접적인 상관관계를 보이지 않았습니다.
* 특징 중요도: 머신러닝 모델은 **스트레스 지표(예: 업무 압박, 경제적 부담)**와 **인구통계적 특성(예: 연령, 직업)**을 정신 건강에 중요한 영향을 미치는 것으로 나타났습니다.. 이는 경제저거 환경 요인이 인구 구성을 변화시키고, 이 변화가 정신건강 특성 차이를 만드는 데 기여할 수 있음을 시사합니다.

* **Demographics:** Significant differences were observed in age, profession, and education distribution between urban and rural areas. Urban areas showed a higher proportion of young adults (18-25) and students, while rural areas had more education professionals and a higher percentage of post-graduate degree holders, suggesting a return to rural areas after higher education.
* **Lifestyle Indicators:** While urban residents often worked excessively, surprisingly, they reported better dietary habits than rural residents. Sleep deprivation was common in both areas.
* **Stress Indicators:** Urban residents reported significantly higher levels of work performance pressure and financial burden compared to rural residents.
* **Mental Health Indicators:** Statistically significant differences were found. While rural areas showed a slightly higher incidence of suicidal thoughts, urban areas exhibited a higher prevalence of general depression.
* **Correlation Analysis:** No strong direct correlation was found between lifestyle/stress indicators and mental health indicators based on the current dataset.
* **Feature Importance:** Machine learning models consistently identified **stress indicators (e.g., work pressure, financial burden)** and **demographic characteristics (e.g., age, profession)** as the most influential factors impacting mental health. This suggests that socio-economic factors influencing population composition might be key drivers of mental health differences between regions.

## Conclusion & Insights

데이터 분석 결과, 비록 라이프스타일 일부 지표는 도시가 더 좋게 나왔지만, 스트레스 지표와 종합적인 정신건강 지표에서는 도시가 더 좋지 않은 경향을 보였습니다. 이는 이솝우화 '시골쥐 도시쥐'의 소박함 속 평화가 낫다'는 교훈이 현대 데이터에서도 통계적으로 유의미한 측면이 있음을 보여줍니다.

Despite some unexpected findings (e.g., better lifestyle metrics in urban areas, possibly due to ongoing urbanization in rural areas), our analysis suggests that the core message of "The Country Mouse and the City Mouse" fable — that **simplicity often equates to greater peace** — holds statistical validity for mental health indicators in the Indian context. Urban areas generally showed poorer mental health outcomes despite some lifestyle advantages.

## Code Structure

* `01_DataCleaning.ipynb` : Contains code for data preprocessing,
* `02_EDA_Observation` : EDA, statistical analysis, and result generation.
* `03_ML` : Machine learning model building, and result generation.
* `data/`: Directory for the raw dataset file(s).

## Technologies Used

* Python
* Pandas (Data manipulation and analysis)
* NumPy (Numerical operations)
* Matplotlib (Data visualization)
* Seaborn (Enhanced data visualization)
* scikit-learn (Machine learning models)
* XGBoost (Gradient Boosting framework)
* LightGBM (Gradient Boosting framework)
* Jupyter Notebook

## Limitations & Future Work

* **Dataset Specificity:** The findings are based on a specific dataset from India, limiting generalizability to other countries or regions.
* **Variable Granularity:** The dataset's variable granularity and measurement methods might have limited the ability to find strong direct correlations between certain lifestyle/stress factors and mental health indicators.
* **Future Research:** We recommend future studies to involve more in-depth surveys specifically designed to explore causal relationships between lifestyle, socio-economic factors, and mental health, possibly with a focus on specific regional industrial/economic contexts.

---

**[Kyoungmi Kwon]**
* **GitHub:** [https://github.com/kyoungmikwon]
* **LinkedIn:** [https://www.linkedin.com/in/kyoungmi-kwon-3a666a79]
* **Email:** [aout0827@gmail.com]

