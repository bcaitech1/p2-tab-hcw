# Boost Camp - AI Tech

> ## Stage 2 - 온라인 상점 고객 구매 예측

> ### 2021.4.12 ~ 2021.04.23
>
> ### 2년간의 구매 데이터를 통해 고객의 12월 구매 여부 예측 문제


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
3. [Model](#model)<br>
4. [기타](#etc)<br>

<br>

---


<br>

### 💡 핵심 전략<a name = 'strategy'></a>

 ➡ EDA

 ➡ 시계열 특성을 고려한 Feature Engineering

<br>

---

<br>

### 🏃‍♀️ 성능 향상을 위한 고군분투한 여정 <a name ='fullprocess'></a>

### 1. EDA (Exploratory Data Analysis)<a name='EDA'></a>

➡ 고객, 상품 관점의 EDA 수행

✳ 고객의 구매주기 파악

![image](https://user-images.githubusercontent.com/77056802/125425286-cb0a852f-16f4-4402-9805-272c8370783a.png)

✳ 한달 평균 구매 금액 

![image](https://user-images.githubusercontent.com/77056802/125425496-a76b6055-d285-4199-8ab0-8e80c1ad9457.png)
![image](https://user-images.githubusercontent.com/77056802/125425700-5d20be71-4858-4ac1-a139-16f16af37c6c.png)

✳ 구매주기에 따른 다음 구매 달과 12월의 차이

![image](https://user-images.githubusercontent.com/77056802/125430482-87fadd59-bc65-41b2-8c7f-7b4f72ce0134.png)



➡ 사후 EDA를 통해 모델 성능 평가



<br>

### 2.Feature Engineering<a name ='FE'></a>

 ➡ 시계열 특성을 고려한 Feature

　✳ 2011년 12월 기준으로 직전 3,6,9,12,15,18,21 개월 동안의 총구매금액(total_sum)

　✳ 

　✳각 Value 값의 통계적 수치

 ➡ 구매주기에 따른 다음 구매 달과 12월과의 차이 Feature(diff_fin)

![image](https://user-images.githubusercontent.com/77056802/125430569-e547ad8a-81e3-4beb-bf5a-374008e90a89.png)


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

