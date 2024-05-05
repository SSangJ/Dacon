# 주제
##### 저해상도 조류 이미지 분류 AI 알고리즘 개발
##### 입력으로 들어오는 저해상도의 64X64 크기의 조류 이미지로부터 종을 분류하는 AI 알고리즘 개발
<br>

# train 폴더
##### 학습용 64x64 저해상도 조류 이미지 15,834장

<br>

# swinv2 설명(resnet model 대비 accuracy 0.8 >> 0.96)

<br>

## 1.데이터 전처리
##### 1) timm 라이브러리로 이용하기 위하여 train.csv파일에 써져있는 label을 가지고 label별로 폴더를 만들어줌
##### 2) BICUBIC를 이용하여 64*64이미지를 256*256로 변환시켜줌
##### 3) data augmentation으로 randaugmentation 사용 

<br>


## 2. 예측 모델(swinv2)
##### 1) lr=0.001
##### 2) StepLR


<br>

