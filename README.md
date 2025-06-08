# A Tale from India: The Country Mouse and the City Mouse - Where is Well-being in Modern Society? 

## Project Overview

이 프로젝트는 고전 이솝우화 '시골쥐 도시쥐'의 메세지를 현대 사회의 데이터로 검증하고자 했습니다.
도시의 풍요로움 뒤에 숨겨진 스트레스와 위험이 시골의 소박한 평화보다 과연 더 나쁜지, 캐글의 Exploring Mental Health Data를 통해 분석했습니다.

This project delves into the timeless wisdom of Aesop's fable, "The Country Mouse and the City Mouse," by examining whether its core message about the hidden stresses of urban life versus the simple peace of rural living still holds true in modern society. I utilize a mental health dataset from India to investigate the well-being of urban versus rural inhabitants.

## Motivation
이 프로젝트는 고전 우화를 현대의 정신 건강 데이터와 연결하여 데이터 분석을 통해 독창적인 탐구를 시도한 것입니다. 
목표는 서로 다른 환경에서의 인간의 웰빙에 대해 겉보기에는 단순하지만 실은 깊은 의미를 가진 질문을 데이터로 풀어보는 것이었습니다. 
이러한 참신한 접근 방식은 많은 관심을 끌었습니다.

This project was initiated as a unique exploration into data analysis, connecting a classical fable with contemporary mental health data. The aim was to use data to address a seemingly simple, yet profound, question about human well-being in different environments. The novelty of this approach garnered significant interest.

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
