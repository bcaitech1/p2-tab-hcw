# Boost Camp - AI Tech

> ## Stage 2 - 온라인 상점 고객 구매 예측

> ### 2021.4.12 ~ 2021.04.23
>
> ### 2년간의 구매 데이터를 통해 고객의 12월 구매 여부 예측 문제

`Boost Camp P stage 2 대회의 과정과 결과를 담은 Git repo 입니다. 대회 규칙상 특정 내용이 수정되거나 삭제된 경우가 존재합니다`

---

<br>

### 🏁 Final Score 

Rank : 24 , AUC : 0.8594

<br>

---



### 📋 Table of content 

##### [핵심 전략](#strategy)<br>

##### [성능 향상을 위한 고군분투한 여정 🏃‍♀️](#fullprocess)

1. [EDA](#EDA)<br>
2. [Feature Engineering](#FE)<br>
3. [Data Augmentation](#aug)<br>
4. [Model](#model)<br>
5. [기타](#etc)<br>

<br>

---


<br>

### 💡 핵심 전략<a name = 'strategy'></a>

 ➡교육 도메인 지식 활용

 ➡User split augmentation

 ➡private leader board를 고려한 모델 실험

 ➡Two track (task cross-reference)

<br>

---

<br>

### 🏃‍♀️ 성능 향상을 위한 고군분투한 여정 <a name ='fullprocess'></a>

### 1. EDA (Exploratory Data Analysis)<a name='EDA'></a>

➡ 다양한 EDA를 통해 Feature engineering과 validation 전략을 세우는데 활용

![image](https://github.com/bcaitech1/p4-dkt-ollehdkt/blob/headbreakz/image/EDA.gif?raw=true)

<br>

### 2.Feature Engineering<a name ='FE'></a>

 ➡ 데이터 분석 기반 Feature

　✳ User ID, assessmentItemID, testId, KnowledgeTag, Timestamp 과 answerCode 관계

　✳각 Value와 answerCode값의 평균, 분산, Skew, 누적합, 누적 평균

　✳각 Value 값의 통계적 수치

 ➡ 교육학 이론 기반 Feature

　✳assessmentItemID, testId, KnowledgeTag의 변별도 값 

　✳변별도 : (상위 정답 수 - 하위 정답 수 ) / (총 응시자 / 2)

➡ ELO rating

　✳정답 여부에 따른 개인 Rank 점수 적용

　✳문제 난이도에 따른 Rank 점수의 증가와 감소

➡ 총 47개의 Feature 생성

➡ [Feature Engineering 상세](https://www.notion.so/Feature-Engineering-0189914b580a483083b88982006984d6)

![image](https://github.com/bcaitech1/p4-dkt-ollehdkt/blob/headbreakz/image/FE.png?raw=true)

<br>

### 3. Data augmentation <a name = 'aug'></a>

➡ Sliding Window(Stride = 10,20, ... ,128)

➡ User month split (사용자를 월별로 정리)

➡ User testID grade split (사용자를 문제지별 정리)

<br>

### 4. Model <a name = 'model'></a>

➡ Tree decision : LGBM , XGBoost , Catboost

➡ NN Models : LSTM , LSTM with Attention , Bert , Saint , GPT-2, LastQuery_pre/post

![image4](https://github.com/bcaitech1/p4-dkt-ollehdkt/blob/headbreakz/image/model.png?raw=true)

<br>


### 5. 기타 <a name = 'etc'></a>

➡ permutation Feature Selection




<br>

---

### Reference

[Deep Knowledge Tracing](https://arxiv.org/pdf/1506.05908.pdf)

[BERT](https://arxiv.org/abs/1810.04805)

[Bayesian Opitimization](https://arxiv.org/pdf/1807.02811.pdf)

[Saint+](https://arxiv.org/pdf/2010.12042.pdf)

[EGNET+KT1](https://arxiv.org/pdf/1912.03072.pdf)

---

