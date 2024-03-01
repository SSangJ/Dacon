# 주제
##### 학습 플랫폼 구독자 예측 AI 해커톤
##### 이용자의 구독 기간, 로그인 활동, 학습 세션 참여도와 같은 데이터 분석을 통해 학습 플랫폼 이용자의 구독 갱신 여부를 예측하는 AI 모델을 개발해야 합니다.
<br>

# train.csv
##### user_id:	사용자의 고유 식별자
##### subscription_duration:	사용자가 서비스에 가입한 기간 (월)
##### recent_login_time:	사용자가 마지막으로 로그인한 시간 (일)
##### average_login_time: 	사용자의 일반적인 로그인 시간
##### average_time_per_learning_session:	각 학습 세션에 소요된 평균 시간 (분)
##### monthly_active_learning_days:	월간 활동적인 학습 일수
##### total_completed_courses:	완료한 총 코스 수
##### recent_learning_achievement: 	최근 학습 성취도
##### abandoned_learning_sessions:	중단된 학습 세션 수
##### community_engagement_level:	커뮤니티 참여도
##### preferred_difficulty_level:	선호하는 난이도
##### subscription_type:	구독 유형
##### customer_inquiry_history:	고객 문의 이력
##### payment_pattern
##### 사용자의 지난 3개월 간의 결제 패턴을 10진수로 표현한 값.
- 7: 3개월 모두 결제함
- 6: 첫 2개월은 결제했으나 마지막 달에는 결제하지 않음
- 5: 첫 달과 마지막 달에 결제함
- 4: 첫 달에만 결제함
- 3: 마지막 2개월에 결제함
- 2: 가운데 달에만 결제함
- 1: 마지막 달에만 결제함
- 0: 3개월 동안 결제하지 않음
##### target:사용자가 다음 달에도 구독을 계속할지 (1) 또는 취소할지 (0)를 나타냄

# 데이터 전처리 및 모델 설명

##### 이 문서는 데이터 전처리 및 모델 선택에 대한 접근 방식을 설명

## 1.데이터 전처리
##### 1-1) 데이터 정제 : 사용하지 않을 user_id는 제거해 주었음
##### 1-2) preferred_difficulty_level column은 서열이 존재하는 categorical data이므로 label encdoing해주었음
##### 1-3) 스케일링 : 수치형 변수에 대해 Min-Max Scaling 표준화를 적용하여 변수간 스케일 조정
##### 1-4) 결측치 대체 : 평균값 등으로 대체를 하면 좋지 않은 영향을 미칠것 같아 0으로 대체하였음
##### 1-5) 데이터 불균형 : 구독 예측 train.csv파일에 데이터 불균형이 존재하여 RandomOverSampler를 진행하였으나 다른 것으로 진행하였으면 조금더 좋은 성능의 모델이 나왔을것으로 예상 된다.


## 2. 예측 모델
##### 1-1) tensorflow MLP model 이용
##### 1-2) layer수, layer 깊이, batchnormalization, l1,l2, dropout 등을 바꾸어 가며 최적의 파라미터 튜닝 진행
##### 1-3) EarlyStopping 이용
##### 1-4) ReduceLROnPlateau learning rate schedluer 사용






