# 제주렌트카 가격예측 회귀분석 프로젝트


## 파일설명

### 데이터수집

#### [제주렌트카 프로젝트 크롤링](https://github.com/GS-Jo/Reg-Project/blob/main/regression_project_selenium.ipynb)

### EDA 및 모델링 파일

#### [제주렌트카 프로젝트 전처리](https://github.com/GS-Jo/Reg-Project/blob/main/preprocessing_Rentcar.ipynb)

#### [제주렌트카 프로젝트 EDA&모델링](https://github.com/GS-Jo/Reg-Project/blob/main/EDA_Modeling.ipynb)

#
## 1.주제 선정

### 1-1. 문제인식
  - 코로나 이슈로 해외여행의 대체재로 제주도여행 수요가 몰리면서 제주도 렌트카 가격이 급증하고있다.
  - 올 여름 여행을 위해 렌트카 가격을 미리 예측하여 가성비갑 여행을 해보자!

   
#
## 2. 데이터 설명
### 2-1. 데이터 수집
- 데이터 수집 사이트 : 제주패스랜트카
![스크린샷 2021-06-08 오후 4 43 55](https://user-images.githubusercontent.com/80459891/121144609-1c84df00-c879-11eb-929e-b88078eefb05.png)
- 수집기간 : 6월~10월
- 수집방법 : 크롤링(selenium, bs4)
#
### 최초 데이터 변수 설명
### 독립변수(17개)  / 주요 독립변수 : "차량가격"
- 모델명 | 세그먼트 | 수용인원 | 연료타입 | 제공업체 | 랜트가능 최소 연령 |
- 옵션개수 | 리뷰수 | 누적예약수 | 별점 | 일자 | 요일 | 취급렌트카수 | 연식 |
- 평일/휴일 | 비수기/성수기 | 
- 옵션종류 | 월 | 차량가격
### 종속변수
- 하루 렌트 가격
### 1개 row 데이터 도식화
![스크린샷 2021-06-08 오후 4 43 06](https://user-images.githubusercontent.com/80459891/121144596-17c02b00-c879-11eb-8e4e-8edf04fa9adf.png)
![스크린샷 2021-06-08 오후 4 42 52](https://user-images.githubusercontent.com/80459891/121144545-0c6cff80-c879-11eb-95ff-a1095a511700.png)

#
## 3. 데이터 전처리

<img width="1027" alt="스크린샷 2022-05-18 오후 12 54 11" src="https://user-images.githubusercontent.com/80455724/168954702-e7ab16e8-04a7-4a4c-b186-d0bdbac5a9c4.png">

#### - 성수기/비수기 컬럼 추가: 렌트가격이 다르게 책정되는 7월15일부터 한달간을 '성수기'로 정하여 컬럼 추가
#### - 평일/휴일 컬럼 추가: 여행수요가 증가하는 금/토일/공휴일을 휴일로 하여 컬럼 추가
#### - 옵션컬럼 수정: 차량 옵션 컬럼들을 drop하고 옵션갯수컬럼 추가


## 4. 데이터 탐색(EDA)

#### EDA에 앞서 가설을 세워보자.
* 가설1. 차량모델의 가격이 비쌀수록 렌트가격이 높을 것이다.
* 가설2. 성수기에는 평시에 비해 렌트가격이 더 비쌀 것이다.
* 가설3. 평일보다 휴일에 가격이 더 비쌀 것이다.
* 가설4. 부가옵션이 많이 붙은 차량일수록 가격이 비쌀 것이다.
* 가설5. 렌트가능나이가 낮을수록 렌트가격이 저렴할 것이다.
* 가설6. 연식이 오래된 모델일수록 렌트가격이 저렴할 것이다.
* 가설7. 취급업체가 많은 모델일수록 상대적으로 렌트가격이 저렴할 것이다.

<img width="1018" alt="스크린샷 2022-05-18 오후 12 55 37" src="https://user-images.githubusercontent.com/80455724/168955478-8e2fca8d-d6be-44d5-aa73-9d0d935fec95.png">

#### - 차량 모델의 가격

<img width="1006" alt="스크린샷 2022-05-18 오후 12 55 45" src="https://user-images.githubusercontent.com/80455724/168955381-f097ebf0-4da9-451c-87bb-9768721c3b96.png">

#### - 성수기/비수기

<img width="1017" alt="스크린샷 2022-05-18 오후 1 21 10" src="https://user-images.githubusercontent.com/80455724/168956784-f0333ee4-291e-48ec-b00b-8721a0bcdd53.png">

#### - 차량의 모델 연식

<img width="1020" alt="스크린샷 2022-05-18 오후 12 56 05" src="https://user-images.githubusercontent.com/80455724/168955535-7451a694-1e53-4d7e-9253-8f56cab929c5.png">
#### - 차종

<img width="1007" alt="스크린샷 2022-05-18 오후 12 56 20" src="https://user-images.githubusercontent.com/80455724/168955562-f4deff0a-088a-4bb7-91a9-474c166f503c.png">

#### - 차량에 포함된 옵션갯수

<img width="1011" alt="스크린샷 2022-05-18 오후 1 22 20" src="https://user-images.githubusercontent.com/80455724/168956806-f9634923-f4d8-40f0-b0a2-6d59c386bf6f.png">

#### - 차량의 취급업체 수

해당 컬럼들은 렌트가격 형성과 주요한 상관관계가 있음을 확인함.



## 5. 가격예측 모델링


### 5-1. 베이스라인 설정

#### - 데이터 EDA를 통해 확인한 주요 수치형 컬럼들만으로 모델링하여 베이스라인을 확인
- 차량 모델의 가격
- 성수기/비수기
- 차량의 모델 연식
- 차량에 포함된 옵션갯수
- 차량의 취급업체 수

![download](https://user-images.githubusercontent.com/80455724/168955795-95fb8301-3f53-4596-8ad2-cbbe7e4718d1.png)
#### 랜덤포레스트 리그레서 기준 - 약 16000원 정도의 오차를 보임.
- RMSE of test : 16733.335667386735 - 베이스라인으로 설정

#
### 5-2. 전체 데이터 활용
#### 모델의 가격예측성능을 높이기 위해 다음과 같은 방법으로 수치형데이터 전처리를 시도해보았음.
- 첫번째 시도1. 모든 범주형 데이터 더미변수화
- 두번째 시도2. 일부 컬럼 라벨 인코딩 + 범주형 데이터 더미변수화 
- 세번째 시도3. 일부 컬럼 카테고리임베딩 + 더미변수화

### 카테고리데이터 수치화 방법1 : 범주형 데이터를 모두 one-hot incoding을 통해 수치형으로 변환
#### OLS summary 
- R-squared : 0.933
#### Linear Regressor 
- train RMSE : 26591.34
- test RMSE : 26736.88
#### RandomForest Regressor
- train RMSE : 7383.02
- test RMSE : 11620.82
#

### 카테고리데이터 수치화 방법2 : 범주형 데이터를 모두 one-hot incoding + 라벨인코딩을 통해 수치형으로 변환

#### OLS summary 
- R-squared : 0.788
### Linear Regressor 
- train RMSE : 47168.96
- test RMSE : 45884.44
#### RandomForest Regressor
- train RMSE : 7385.26
- test RMSE : 11562.87

<img width="998" alt="스크린샷 2022-05-18 오후 1 20 53" src="https://user-images.githubusercontent.com/80455724/168956742-42cc9bd9-c43f-4ad0-a61d-1b42b4d1efee.png">


#
### 카테고리데이터 수치화 방법3 : 범주형 데이터를 모두 one-hot incoding + 카테고리 임베딩을 통해 수치형으로 변환
#### OLS summary 
- R-squared : 0.784
#### Linear Regressor 
- train RMSE : 47617.61
- test RMSE : 46335.77
#### RandomForest Regressor
- train RMSE : 7377.90
- test RMSE : 11651.45
#
### 최적의 데이터 전처리 방법 및 모델
- 데이터 전처리 방법 : 범주형 데이터를 모두 one-hot incoding + 카테고리 임베딩을 통해 수치형으로 변환
- 최적의 모델 : RandomForest Regressor
- R-squared : 0.784
- RMSE : 11651.45

### K-fold 교차검증
- cv_rmse : [11823.147750024658, 23222.38593124356, 35213.191847925475, 23541.66932410497, 24185.23807694114]
- K-fold 평균 RMSE : 23597.12658604796


