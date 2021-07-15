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

 ➡ 사전 EDA / 사후 EDA

 ➡ 시계열 특성을 고려한 Feature Engineering
 
 ➡ CV 전략 : Stratified k-fold

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

 ➡ 각 Value 값의 통계적 수치

 ➡ 시계열 특성을 고려한 Feature

　 ✳ 2011년 12월 기준으로 직전 3,6,9,12,15,18,21 개월 동안의 총구매금액(total_sum)
 
   ✳ label별 total_12 값의 분포 차이 존재

![image](https://user-images.githubusercontent.com/77056802/125777678-c31f26e8-2c35-4ff4-b271-cc63b73749b4.png)


 ➡ 구매주기에 따른 다음 구매 달 예측 결과와 12월과의 차이 Feature(diff_fin)
 
   ✳ label별 diff_fin 값의 분포 차이 존재

![image](https://user-images.githubusercontent.com/77056802/125430569-e547ad8a-81e3-4beb-bf5a-374008e90a89.png)


 ➡ 상품별 중요도 Feature(prd_imp_total)
 
   ✳ 많이 주문되는 상품 순위를 중요도로 판단
   
   ✳ 중요도 = 평균 판매수량 * 단가
   
   ✳ label별 분포 차이 존재 X 

![image](https://user-images.githubusercontent.com/77056802/125780866-4cef7ff7-e0c2-4520-b577-c20349760574.png)


<br>

### 3. Model <a name = 'model'></a>

➡ Tree decision : LGBM , XGBoost

  ✳ LGBM이 빠르고 성능이 높은 것을 확인한 결과, LGBM을 주모델로 사용 
  
➡ Cr
  
  ✳ 평가지표 AUC 점수 상승

![image](https://user-images.githubusercontent.com/77056802/125779518-5c9a63c1-69d0-4831-a2f1-bd5774c572f6.png)



<br>


### 5. 기타 <a name = 'etc'></a>

➡ Feature Selection

  ✳ permutation Feature Selection (from eli5.sklearn import PermutationImportance)
  
  ✳ Correlation Feature Selection : Feature간의 상관계수를 통해 Feature select
  

➡ PCA




<br>

---

### Reference

---

