# 주제
##### C++ 코드간의 유사성을 판단할 수 있는 AI 알고리즘 개발
##### 두개의 C++ 코드 쌍이 동일한 문제를 해결하는 코드인지 유사성을 판단하는 AI 알고리즘 개발
<br>

# train.csv
#####  code1 : 유사성을 비교할 C++ 코드 1
#####  code2 : 유사성을 비교할 C++ 코드 2
#####  similar : 0일 경우 서로 다른 문제를 해결하려는 코드, 1일 경우 서로 같은 문제를 해결하려는 코드

<br>

# Baseline 코드 설명(accuracy : 0.6)
##### 이 문서는 데이터 전처리 및 모델 선택에 대한 접근 방식을 설명

<br>

## 1.데이터 전처리
##### 1) CountVectorizer() 를 이용하여 vectorizer 학습한 후, vocabulary.update로 어휘 추가
##### 2) cosine_similarity 를 통하여 벡터간 코사인 유사도를 계산
<br>


## 2. 예측 모델(BaselineModel)
##### 1) get_vectorizer : 어휘집합을 기반으로 새 countvectorizer객체 생성
##### 2) fit : 코드 샘플을 받아 모델 어휘 집합 업데이트
##### 3) predict_proba : 두 코드 샘플간의 코사인 유사도 계산
##### 4) predict : predict_proba로 부터 받은 유사도 점수가 임계값보다 높으면 1, 낮으면 0 

<br>



# graphcode_bert 설명(accuracy 0.75)

<br>

## 1.데이터 전처리
##### 1) clean_data 라는 함수 정의하여 C++ 코드 전처리(c++ 코드에 대한 이해도가 낮아 높은 수준의 전처리는 하지 못하였음)
##### 2) pretrained 토큰화 모델을 로드하여 긴 텍스트는 왼쪽 끝부터 텍스트를 잘라 pair쌍을 만들어준다
##### 3) 이후 pytorch tensor로 변환해주고 모든 입력 길이를 512로 만들어준다.
##### 4) bert의 입력으로 사용될 input_ids와 attention_masks를 만들어준다.

<br>

## 2. 예측 모델(BaselineModel)
##### 1)AutoModelForSequenceClassification 를 이용하여 graphcodebert 모델 이용
##### 2)AmdaW 이용

