# 주제
##### 다양한 개인적 특성을 바탕으로 한 데이터를 활용하여 소득 수준을 예측
##### 개인 특성 데이터를 활용하여 개인 소득 수준을 예측하는 AI 모델 개발
<br>

# train.csv
##### ID
##### AGE
##### Gender
##### Education_Status
##### Race
##### Hispanic_Origin
##### Martial_Status
##### Household_Status
##### Household_summary
##### Citizenship
##### Birth_Country
##### Birth_Country(Father)
##### Tax_Status
##### Income (Target)

<br>

# 데이터 전처리 및 모델 설명
##### 이 문서는 데이터 전처리 및 모델 선택에 대한 접근 방식을 설명

<br>

## 1.데이터 전처리
##### 1-1) 대부분의 column이 수많은 변수들을 가지는 categorical features 이므로 label encoding과 target encoding 중 target encoding으로 결정
##### 1-2) 적은 변수 가짓수를 가지는 categorical feature는 one-hot encoding
##### 2) Gains와 income의 이상치를 처리해 주기 위해 너무 큰 값은 잘라 주었음



## 2. 예측 모델
##### 1-1) xgboost,lightgbm,random_forest,gradient_boosting,catboost 모델 이용
##### 1-2) optuna를 이용하여 최적의 파라미터를 찾고 위에서 언급한 모델들의 앙상블 진행
##### 1-3) 100보다 적은 수익을 가지는 column은 거의 없기 때문에 100보다 작으면 0으로 변경

