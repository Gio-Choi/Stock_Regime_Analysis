## 소프트웨어융합캡스톤디자인
## 금융데이터를 활용한 주식 시장 국면 분석
### 요약
#### [1. 과제 개요](#1-과제-개요)
#### [2. 과제 주요 내용](#2-과제-주요내용)
#### [3. 수행 결과](#3-수행-결과-1)
#### [4. 기대 효과 및 활용 방안](#4-기대-효과-및-활용-방안-1)
#### [5. 결론 및 제언](#5-결론-및-제언-1)

## 1. 과제 개요
###  과제 설계 배경 및 필요성: 

Historical Data로 주식 시장의 국면을 분석하려는 연구는 활발히 진행되고 있다. 하지만 정상성이 확보되며 빅데이터를 활용 가능한 컴퓨터 비젼, 자연어 처리에 비해 높은 성능을 못 내고 있음도 사실이다. 본 연구에서 활용하려는 거시 지표의 경우, 일년에 몇 번 발표되는 것도 존재하기에 데이터의 양이 부족하며, 다양한 거시 지표의 종류에 비해 양이 부족하기에 차원의 저주에 빠지기도 한다. 또한 데이터의 양을 확보하기 위해 오래 전부터 축적된 많은 데이터를 활용한다고 해도 분석에 유의미한 영향을 끼칠 수 없을 수 있다. 현재와는 동떨어진 분석이 될 수 있기 때문이다. 그럼에도 불구하고, 산업과 학계에서 이러한 퀀트 분석은 적극 활용되고 있으며 앞으로도 발전이 기대되는 분야다. 따라서 본 연구는 선형회귀부터 RandomForest, Deep Neural Network (DNN)을 비롯한 머신러닝을 활용해 국면을 분석해보고 모델들을 세부 튜닝해 성능을 최대한 높이는 것을 목표로 한다.  

### 과제 주요 내용:

거시 경제 지표들을 활용해 주식시장 국면의 상승 혹은 하락을 분류해본다. 이를 위해 머신러닝 모델들을 활용해 분석을 진행한다. 

### 최종결과물의 목표:

Logistic Regression을 성능을 벤치마크로 하며 DNN과 RandomForest 모델을 튜닝해 벤치마크보다 높은 성능을 내도록 한다. 
 
 ## 2. 과제 주요내용
 ### 개발 환경 및 언어 : 
 개발 환경 : Colab, Jupyter Notebook
 
 언어 : 파이썬
 
 ### 데이터 셋 :
 
 독립변수로는 총 10개의 거시 경제 지표를 활용하였습니다. 사용한 거시 경제 지표는 변동성 지수, 소비자물가지수, M2통화량, 기준금리, 장단기 금리 스프레드, 회사채, 실업률, 생산자물가지수, 수출 물가지수입니다. 종속 변수인 주식 시장을 국면을 나타낼 변수로는 S&P 500 지수를 사용했습니다. 각 데이터의 출처는 참고 자료[6]에 전부 표기해 두었습니다. 각 독립변수로 어떤 데이터를 사용할지는 선행연구와 FRED에서의 이용량을 기준으로 정했습니다. 
 
 모든 데이터셋은 pandas_datareader.data 모듈을 통해 FRED와 yahoo finance에서 수집했습니다. 수집 기간은 모듈이 제공하는 가장 이른 시기인 2004년 1월 1일부터 2020년 12월 31일까지로 했습니다. 사용한 거시지표의 발표 주기가 최대 한 달이기에 분석의 time step을 1달로 두었습니다. Null 값이 있는 데이터를 보간해보는 시도도 해보았지만 금융데이터의 특성 상 보간은 진행하지 않았습니다. 최종적으로, 사용한 데이터의 개수는 201개입니다. 매달 하나씩 데이터가 나오기에 양이 부족하였고 분석을 진행하던 초기에 성능이 낮게 나오게 한 이유 중 하나라 생각합니다. 

 
 |종류|출처|
 |---|---|
 |Stock Regime|[S&P500](https://finance.yahoo.com/quote/%5EGSPC/)|
 |Volatility Index| [CBOE Volatility Index: VIX](https://fred.stlouisfed.org/series/VIXCLS)|
 |Consumer Price Index|[Consumer Price Index for All Urban Consumers: All Items in U.S. City Average](https://fred.stlouisfed.org/series/CPIAUCSL)|
 |M2|[Board of Governors of the Federal Reserve System (US), M2](https://fred.stlouisfed.org/series/M2SL)|
 |Federal Fund Effective Rate|[Board of Governors of the Federal Reserve System (US), Federal Funds Effective Rate](https://fred.stlouisfed.org/series/FEDFUNDS)|
 |Interest Rate Spreads|[ 10-Year Treasury Constant Maturity Minus 2-Year Treasury Constant Maturity ](https://fred.stlouisfed.org/series/T10Y2Y)|
 |Corporate Bond|[Moody's Daily Corporate Bond Yield Averages](https://fred.stlouisfed.org/series/AAA)|
|Unemployment Rate|[U.S. Bureau of Labor Statistics, Unemployment Rate](https://fred.stlouisfed.org/series/UNRATE)|
|Producer Price Index|[U.S. Bureau of Labor Statistics, Producer Price Index by Industry: Total Manufacturing Industries](https://fred.stlouisfed.org/series/PCUOMFGOMFG)|
|Coincident Economic Activity Index|[Federal Reserve Bank of Philadelphia, Coincident Economic Activity Index for the United States](https://fred.stlouisfed.org/series/USPHCI)|
|Export Price Index|[U.S. Bureau of Labor Statistics, Export Price Index (End Use): All Commodities ](https://fred.stlouisfed.org/series/IQ)|

((추가예정)) 각 데이터 셋의 분포를 맷플롯립으로 시각화한 그림. 

((추가예정)) x값 10가지와 Y값이 모두 담긴 데이터 프레임 그림. 

### Output: 

종속변수인 S&P 500 지수가 저번 달 대비 이번 달의 변화율이 음수면 0, 0보다 크거나 같으면 1로 라벨링하였고 아래와 같은 모델들을 통해 classification을 진행했습니다. 매달 영업일 기준 첫 날을 기준으로 하였습니다.

### DNN:

은닉층의 설계를 어떻게 할지 Gu et.al 를 참고했습니다. [1] 피라미드 구조와 같이 은닉층의 뉴런의 개수가 점차 줄도록 설계했습니다. 최종적으로 32, 16, 8, 4, 2가 가장 성능이 높았습니다. 또한 활성화함수는 elu를 사용하였고 Loss function은 binary_crossentropy를, optimizer는 nadam을 사용하였습니다. 

하이퍼파라미터 튜닝을 어떤 기준으로 할지는 Gu et.al 를 참고했으며 validation set을 기준으로 성능이 가장 높은 하이퍼파라미터를 택했습니다. 이를 위해 학습을 진행할 때 검증 데이터의 정확도가 이전보다 좋아진 경우에만 모델을 저장하도록 했습니다. 최종 하이퍼 파라미터는 batch_size 8, epoch 400입니다. 
     
   오버피팅을 막기 위해서는 K fold cross validation (split 5)을 진행했습니다. Cross validation이 아닌 단순히 train set과 test set을 8대2 비중으로 나누고도 분석을 진행했습니다.  이외에도, BatchNormalization과 Drop out도 적용했습니다. 입력층과 은닉층 이후 매번 Batchnormalization을 진행했고, Drop out의 비율은 0.2로 했습니다. 

((추가예정)) 최종적으로 사용한 Neural Network의 구조 사진. 

((추가 예정))Batch Normalization과 Drop out에 관한 설명.

### Random Forest:

Random Forest는 맨 처음 Scikit-learn의 디폴트 설정으로 분석을 진행해보았지만 성능이 너무 낮게 나와 파라미터들을 조정해가며 성능을 올려보았습니다. 이를 위해 가능한 파라미터들을 전부 리스트로 넣어준 후 RandomizedSearchCV를 활용해 어떤 파라미터의 조합이 가장 성능이 높게 나오는지 테스트해보았습니다. 

분석해본 경우의 수를 말하자면, 생성할 결정트리의 개수(n_estimators)는 200개부터 10을 증가해가며 2000개까지 증가해보았으며, 결정트리의 깊이(depth)는 10부터 11개씩 늘려가며 110까지 늘려보았고, 하나의 leaf에 들어갈 최소 샘플 개수는 1,2,4로 설정했으며, 노드를 split할 때 해당 노드의 최소 샘플 개수는 2, 5, 10으로 해보았습니다. 또한 Bootstrap여부도 True, False로 넣어주었습니다. 이러한 설정 하에 1000번 iteration을 돌려보았고 3 fold cross validation을 진행했습니다. 

그 결과 최종적으로 선택한 파라미터는 n_estimators 800, min_samples_split 10,  min_samples_leaf 4, max_depth 50, bootstrap: True 입니다.

((추가 예정)) 랜덤포레스트 모델 그림으로 보여주기

## 3. 수행 결과
### 과제수행 결과:

모델들을 튜닝하지 않고 Scikit-learn과 Keras의 디폴트 설정으로 분석을 진행했을 때 성능이 낮게 나왔다. 하지만 2. 과제 수행 방법에서 언급한 시도들을 하나씩 해보며 최종적으로 test set 대상 정확도가 Logistic Regression은 0.74, DNN 0.78, Random Forest는 0.71이 나왔다.

### 최종결과물 주요특징 및 설명:

DNN이 가장 우수한 성능을 나타냈다. 10개의 거시경제변수와 국면 간의 비선형적인 관계를 DNN 모델이 가장 잘 파악했다고 볼 수 있다. 


## 4. 기대 효과 및 활용 방안
### 기대 효과:

Test set 대상 정확도가 0.78을 기록하였으므로 국면을 분석하는 모델을 만들었다 평가할 수 있다. 따라서 DNN 모델을 활용해 이번 달의 거시경제 데이터로 다음 달의 국면을 분석해 볼 수 있다. 또한 DNN과 RandomForest를 튜닝하는 방법은 이번 주제 이외에도 다른 도메인의 데이터로 Classification을 수행할 때 활용 가능하다.

### 활용 방안:

이러한 국면 분석을 기반으로 실제 투자에도 적용해 백테스트를 진행해볼 수 있다. 가령, 다음 달의 주식 시장 국면이 하락으로 예상될 때 sell했다가 국면이 상승으로 전환될 것이라 분석될 때 buy해 최종적으로 수익률을 buy&hold 전략과 비교해볼 수 있다.

   
## 5. 결론 및 제언

DNN과 Random Forest를 활용해 주식시장 국면을 분석해보았다. 모델들을 튜닝해 최종적으로 0.78의 정확도를 갖는 성능을 만들었다. 이를 위해 DNN의 경우 Batch Normalization, Drop Out, 뉴런의 개수 조정, K-fold Cross Validation을 시도해보았다. RandomForest는 RandomizedSearchCV를 활용해 생성할 결정트리의 개수(n_estimators), 결정트리의 깊이(depth), 하나의 leaf에 들어갈 최소 샘플 개수, 노드를 split할 때 해당 노드의 최소 샘플 개수, Bootstrap여부의 조합으로 테스트 해보았다. 
 향후 계획으로는 거시경제지표 뿐만이 아닌 모멘텀 지수와 같은 기술적 지표도 추가해 볼 예정이며 거시경제지표의 개수를 더 늘릴 계획이다. 또한 앞서 언급했듯 국면이 하락으로 예상될 때 매도했다가 상승으로 예상될 때 매수를 해서 백테스트 해보고 다른 투자 전략들과 비교도 해볼 수 있다.


## References 

[1] Gu, Shihao, Bryan Kelly, and Dacheng Xiu. "Empirical asset pricing via machine learning." The Review of Financial Studies33.5 (2020): 2223-2273.

[2] Botte, Alex, and Doris Bao. "A Machine Learning Approach to Regime Modeling." Two Sigma (2021).

[3] Jiang, Manrui, et al. "The two-stage machine learning ensemble models for stock price prediction by combining mode decomposition, extreme learning machine and improved harmony search algorithm." Annals of Operations Research(2020): 1-33.

[4] Gerlein, Eduardo A., et al. "Evaluating machine learning classification for financial trading: An empirical approach." Expert Systems with Applications 54 (2016): 193-207.

[5] Géron, Aurélien. Hands-on machine learning with Scikit-Learn, Keras, and TensorFlow. " O'Reilly Media, Inc.", 2022.

[6] ‘금융데이터분석’ (SWCON424-00) 수업 자료


