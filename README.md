## 소프트웨어융합캡스톤디자인
## 금융데이터를 활용한 주식 시장 국면 분석
### 요약
#### [1. 과제 선정 배경 및 필요성](#1-과제-선정-배경-및-필요성)
#### [2. 과제 주요 내용](#2-과제-주요내용)
#### [3. 수행 결과](#3-수행-결과-1)
#### [4. 기대 효과 및 활용 방안](#4-기대-효과-및-활용-방안-1)
#### [5. 결론 및 제언](#5-결론-및-제언-1)

## 1. 과제 선정 배경 및 필요성 
Historical Data로 주식 시장의 국면을 분석하려는 연구는 활발히 진행되고 있다. 하지만 정상성이 확보되며 빅데이터를 활용 가능한 컴퓨터 비젼, 자연어 처리에 비해 높은 성능을 못 내고 있음도 사실이다. 본 연구에서 활용하려는 거시 지표의 경우, 일년에 몇 번 발표되는 것도 존재하기에 데이터의 양이 현저히 부족하며, 다양한 거시 지표의 종류에 비해 양이 부족하기에 ‘차원의 저주’에 빠지기도 한다. 또한 데이터의 양을 확보하기 위해 오래 전부터 축적된 많은 데이터를 활용한다고 해도 분석에 유의미한 영향을 끼칠 수 없을 수 있다. 현재와는 동떨어진 분석이 될 수 있기 때문이다. 그럼에도 불구하고, 산업과 학계에서 이러한 퀀트 분석은 적극 활용되고 있으며 앞으로의 발전이 기대되는 분야다. 따라서 본 연구는 선형회귀부터 랜덤포레스트, Deep Neural Network (DNN)을 비롯한 머신러닝을 활용해 국면을 분석해본다. 

 ## 2. 과제 주요내용
 ### 개발 환경 및 언어 : 
 개발 환경 : Colab, Jupyter Notebook
 언어 : 파이썬
 ### 데이터 셋 :
 |종류|사용한 데이터 셋|
 |---|---|
 |주식 시장 국면|[S&P500](https://finance.yahoo.com/quote/%5EGSPC/)|
 |VIX| [CBOE Volatility Index: VIX](https://fred.stlouisfed.org/series/VIXCLS)|
 |||



<img src="https://user-images.githubusercontent.com/66895650/147273804-b7e1a537-a725-4a67-89b8-6157f6108478.png" width="25%" height="25%" />



<img width="552" alt="image" src="https://user-images.githubusercontent.com/66895650/147274930-e77166f9-e746-45e2-95d6-04251c45224d.png">





## 3. 수행 결과
#### 모델 별 테스트 셋 정확도




## 4. 기대 효과 및 활용 방안
### 1) 기대 효과

### 2) 활용 방안
   
## 5. 결론 및 제언

## References 

[1] Gu, Shihao, Bryan Kelly, and Dacheng Xiu. "Empirical asset pricing via machine learning." The Review of Financial Studies33.5 (2020): 2223-2273.

[2] Botte, Alex, and Doris Bao. "A Machine Learning Approach to Regime Modeling." Two Sigma (2021).

[3] Jiang, Manrui, et al. "The two-stage machine learning ensemble models for stock price prediction by combining mode decomposition, extreme learning machine and improved harmony search algorithm." Annals of Operations Research(2020): 1-33.

[4] Gerlein, Eduardo A., et al. "Evaluating machine learning classification for financial trading: An empirical approach." Expert Systems with Applications 54 (2016): 193-207.

[5] Géron, Aurélien. Hands-on machine learning with Scikit-Learn, Keras, and TensorFlow. " O'Reilly Media, Inc.", 2022.

[6] ‘금융데이터분석’ (SWCON424-00) 수업 자료


