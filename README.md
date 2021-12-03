# Regression_Project

## 제주패스렌트가 (제주렌트카 가격비교사이트) 가격예측 프로젝트

### 데이터 수집방법 : 제주패스렌트카 크롤링
### 데이터 수집기간 : 2021/5/1 ~ 2021/8/31
### 변수 선언
- 독립변수 : car_name, car_type(sedan, suv etc), capacity(x인승), fuel_type, rentcar_company, possible_insurance_age, insurance_type, review_count, reservation_count, grade, company_count(해당모델을 취급하는 렌트카 수), day, options
- 종속변수 : lowest_price

### 주말 공휴일 평일 라벨링(성수기/비성수기)
- 5월
    - 공휴일&주말 : 1,5,6,7,8,14,15,19,20,21,22,28,29
- 6월
    - 공휴일&주말 : 4,5,11,12,18,19,25,26
- 7월 :
    - 공휴일&주말 : 2,3,9,10,16,17,23,24,30,31
- 8월 :
    - 공휴일&주말 : 6,7,13,14,20,21,27,28
- 9월 :
    - 공휴일&주말 : 3,4,10,11,17,18,19,20,21,22,23,24,25
