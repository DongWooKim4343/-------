# Linear Regression based Pull-up Analysis

이 프로젝트는 2023년도 울산대학교 전기공학부 의공학전공 의료데이터해석 강의 개인프로젝트 과제의 결과물입니다.

분석 도구로 파이썬을 사용 하였으며, Numpy, matplot 내장 함수를 사용하여 그래프를 그린 후 상관계수와 표준오차를 구해 상관관계를 알아 보았습니다.


# 1. 연구 배경 및 목적

## 1-1 연구 방법

‘턱걸이 최대횟수’를 종속변수로 ‘키’, ‘몸무게’, ‘BMI지수’, ‘인바디점수’를 독립변수로 하여 선형회귀식을 사용하였고 변수 간의 상관관계 정도를 분석하고 데이터를 수집하였습니다. 확보된 데이터를 통해 선형회귀, 표준오차, 상관계수를 계산하여 각 종속변수가 턱걸이 최대횟수에 미치는 영향을 평가한 프로젝트입니다.

턱걸이 최대 횟수는 봉을 잡고 떨어질 때까지 최대로 수행 가능한 횟수로 지정하였습니다.

## 1-2 턱걸이를 분석한 이유
 턱걸이는 도구를 사용하지 않는 상체근육 전체를 골고루 발달시키는 운동이며 제가 가장 좋아하는 운동입니다 하루에 100여개 가까이 턱걸이를 하기도 합니다.

 특히 대근육인 등과 광배근 발달에 최적입니다.
또한 '턱걸이 최대 횟수'는 체력 검정 지표 중 하나로, 체대 입시나 특수부대 지원 시에도 중요한 지표중하나입니다. 이 말은 턱걸이 최대 횟수를 높일 수 있으면 체력검정에서 유리한 결과를 얻을 수 있다는 것 입니다.

## 1-3 가설

(1) 키와 몸무게는 턱걸이 최대 횟수와 상관관계가 없을 것이다.    
단순히 측정된 지표만으로는 상관관계가 없을 것이라고 예상하였습니다.      

(2) BMI 지수는 정상 체중과 과체중 구간에서 턱걸이 최대 횟수와 상관관계가 있을 것이다.      
BMI지수는 키와 몸무게의 비율이기 때문에 상관관계가 있을 것이라고 예상하였습니다.     

(3) 인바디 점수는 턱걸이 최대 횟수와 상관관계가 있을 것이다.      
인바디 점수는 근육량과 관련된 지표이기 때문에 상관관계가 있을 것이락 생각하였습니다.     

(4) 키, 몸무게, BMI 지수, 인바디 점수 순으로 턱걸이 최대 횟수 예측이 정확할 것이다.     
키와 몸무게의 비율, 근육량과 관련된 지표가 상관관계가 클 것이라고 예상하였습니다.     
  
## 1-4 건강지표 설명
(1) BMI 지수     
계산 방법: (몸무게) / (키)^2     
설명: 단순히 키와 몸무게에 따른 비교식으로 체지방과 근육을 고려하지 않는 건강 지표 중 하나입니다.     

(2)인바디 점수      
계산 방법: 80점 - (표준 제지방량 - 제지방량) + (표준 체지방량 - 체지방량)       
설명: 인바디 점수는 80점을 기준으로 체지방률, 근육량, 체중 등의 수치를 종합한 결과값입니다.     
체중 대비 근육량이 높을수록 인바디 점수는 높아지고     
체중 대비 체지방량이 높을수록 인바디 점수는 낮아집니다.           
         


              
# 2. 데이터 수집 방법
## 2-1 방법 1. 직접 수집
![image](https://github.com/DongWooKim4343/Linear-Regression-based-Pull-up-Analysis/assets/106728608/fb762fd0-8113-4dfc-b039-f5436f553baa)

데이터 수집을 위해 실험 대상자의 턱걸이 기록을 직접 측정하였습니다.\
하지만 직접 측정하는 것은 데이터 수집하는데에 한계가 있음

## 2-2 방법 2. Google form 조사
![image](https://github.com/DongWooKim4343/Linear-Regression-based-Pull-up-Analysis/assets/106728608/1d36ad2e-f0a4-4f54-8d19-4d593e5bec00)

턱걸이에 관심이 있는 집단에서 각 지표에대한 데이터 수집을 진행하였습니다.


표본: 울산대학교 에브리타임 '운동, 다이어트 게시판', 인스타그램 해시태그:턱걸이, 맨몸운동, 철봉, 운동,BARIST한국철봉운동(네이버카페), 맨몸운동갤러리 등

## 2-3 표본 선정 이유
초급자가 하기 어려운 턱걸이 운동 특성상, 턱걸이에 대한 경험과 이해가 있는 대상을 피실험자로 선정하였습니다. 초급자 턱걸이 운동에 대한 최대 기록을 잘 모르고, 기록을 안다고 해도 신뢰도가 떨어질 가능성이 높기 때문입니다. 또한, 데이터 수집이 원활하게 이루어지기 위해 턱걸이에 관심이 있는 대상을 피실험자로 선택하여 진행하였습니다. 본 연구에서는 턱걸이 최대 횟수가 중요한 지표이며 집단끼리의 비교가 아니기 때문에, 중급자 이상의 대상을 선정하여도 연구에 무리가 없을 것으로 판단하였습니다.

## 2-4 수집된 데이터 갯수
![image](https://github.com/DongWooKim4343/Linear-Regression-based-Pull-up-Analysis/assets/106728608/95d5a872-a92b-4538-8c3b-c3081c08005a)

키, 몸무게, BMI지수는 총 91개의 데이터가 수집 되었으며, 인바디 검사 기계의 제한적인 보급 장소의 특성상 인바디 점수는 48개의 데이터만 수집되었습니다.

# 3. 분석 결과 및 해석
![image](https://github.com/DongWooKim4343/Linear-Regression-based-Pull-up-Analysis/assets/106728608/4967b837-ef1a-41ad-82d2-34e2b66b0ee7)


## 3-1 키, 몸무게, BMI지수의 분석
91명의 키, 몸무게, BMI의 수집된 데이터를 바탕으로 그래프와 상관계수, 표준오차를 분석하였습니다.

BMI coefficient 값: -0.0268, BMI 표준오차: 7.9787     
키 coefficient 값: -0.1346, 키 표준오차: 7.9089     
몸무게 coefficient 값: -0.0831, 몸무게 표준오차: 7.9540   

91명의 키, 몸무게, BMI의 수집된 데이터를 바탕으로 그래프와 상관계수, 표준오차를 구하였습니다.

분석된 결과 값으로 보았을때, 유의미한 차이가 보이지 않는다.
측정한 결과 값들에 대한 분석은 인바디점수를 포함한 48개의 데이터 분석에서 실시하였습니다.

키, 몸무게, BMI수치는 턱걸이와는 큰 상관이 없는 것으로 보인다, 일반적으로 생각할 때 몸무게가 가벼우면 턱걸이를 더 많이할 것이라고 생각한다. 하지만 값을 볼때 큰 상관이 없습니다. 

몸무게가 많이 나가더라도 근육량이 많으면 턱걸이를 더 잘하기 때문이라고 예상됩니다.  


## 3-2 키, 몸무게, BMI지수, 인바디 점수까지 수집된 데이터의 분석
![image](https://github.com/DongWooKim4343/Linear-Regression-based-Pull-up-Analysis/assets/106728608/12fc7300-5c61-4beb-b9b5-b834222f5004)

BMI coefficient 값: 0.1157, BMI 스탠다드 에러: 7.0352       
키 coefficient 값: -0.0192, 키 스탠다드 에러: 7.0815        
몸무게 coefficient 값: 0.0832, 몸무게 스탠다드 에러: 7.0583       
인바디 coefficient 값: 0.5928, 인바디 점수 스탠다드 에러: 5.704      

키, 몸무게, BMI지수는 상관계수가 -0.1~0.1 사이이다. 이 수치면 상관계수가 모호한 것이 아니라 상관관계가 없다고 생각해도 무방하다. 그나마 BMI 지수의 상관계수가 0.1 수준으로 다른 두 데이터 보다는 높은 수준이지만 이정도 차이는 연구가 개개인의 설문으로 인한 데이터 수집으로 직접 측정시와 똑같은 환경으로 횟수 측정을 못한 오차를 감안할 때, 큰 의미는 없다는 생각이 듭니다.
표준 오차 또한 추세선의 기댓값에서 약 7회 정도씩 차이로 비슷하게 도출 되었습니다.

인바디 점수의 경우 상관계수가 0.59 수준으로 이 수치면 꽤 강력한 상관관계가 있다고 생각합니다. 실제 그래프를 육안으로 확인했을때, 추세선을 따라 턱걸이 최대 횟수가 증가하는 것을 확인할 수 있었습니다.

또한 인바디 점수의 표준오차는 5.7회 정도이며 다른 3가지 건강지표보다 오차가 더 적은편에 속합니다.

## 3-3 가설검증
(1) '키', '몸무게'는 턱걸이 최대 횟수와 상관관계가 없을 것이다.      
키, 몸무게는 물론 BMI 지수까지 전혀 상관이 없었다. 참 

(2) 'BMI지수'는 정상체중-과체중 구간에서 턱걸이 최대 횟수와 상관관계가 있을 것이다.      
BMI 지수는 아쉽게도 전혀 상관관계가 없었다. 거짓

(3) '인바디 점수'는 턱걸이 최대 횟수와 상관관계가 있을 것이다.       
인바디 점수는 매우 강력하게 상관관계가 있었다. 참
 
(4) '키'='몸무게'<'BMI지수'<'인바디점수' 순으로 턱걸이 최대 횟수 예측이 정확할 것이다.     
인바디 점수를 제외한 다른 건강지표는 아무 차이가 없었다. 거짓


# 4. 결론 및 의의
![image](https://github.com/DongWooKim4343/Linear-Regression-based-Pull-up-Analysis/assets/106728608/59fdff71-ca88-4922-9f5d-63053d7edceb)


![image](https://github.com/DongWooKim4343/Linear-Regression-based-Pull-up-Analysis/assets/106728608/e4b675e6-1f38-4a6e-a1f2-1bc170c56d62)

위의 스포츠 관련된 인물 4명은 BMI기준 모두 과체중~고도비만에 속합니다. 
하지만 이들의 알려진 인바디 점수는 일반인들에 비해서 매우 높은 편입니다

또한, 이들은 턱걸이 영상을 찾아보면 기본적으로 10개 이상을 하며, 이상적인 몸매를 가지고 있습니다. 


## 마치며
1. 키와 체중의 비율을 계산한 BMI 지수는 본 연구의 결과로는 아무런 의미가 없는 수치라고 볼 수 있습니다. 
BMI 지수는 키와 체중을 제외한 근육량, 나이, 성별 등 기타요인들을 고려하지않아 신뢰도가 많이 떨어진다고 생각됩니다.

2. 인바디점수(체중 대비 근육량의 비율이) 높을수록 체력 검사에서 유리하며 이것은 단순 몸무게가 높을수록, 낮을수록이 아닌 몸무게에서 근육량의 비율을 늘려야 턱걸이를 잘하는 건강한 몸이라고 볼 수 있습니다.

3. 턱걸이 최대 횟수를 많이 하기 위한 건강한 몸은 인바디 점수가 높다는 것이며 체중에 비해서 근육량의 비율이 높은 몸이라는 뜻이고, 또한 인바디 점수가 높을수록 턱걸이 최대 횟수가 높은편 이라는 것은 각종 체력기준표에서 고득점을 받을수 있으며 육안으로 봤을때도 이상적인 몸일 확률이 높습니다.

4. 이 연구의 결과로 볼 때, 운동시 체지방은 감소시키고 근육량을 키워야 바람직 하다고 생각이 듭니다.
