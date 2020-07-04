### pandas 라이브러리 다루기



### pandas 라이브러리란?

* 테이블형 데이터를 다룰 수 있는 다양한 기능을 가진 라이브러리
  * 파이썬 데이터 분석을 위해 기본적으로 사용하는 라이브러리
* raw data 를 데이터 분석 전과정을 위해 사용할 수 있도록 변환하는 데이터 전처리에도 많이 사용됨
  * 보통 데이터 분석 목적에 맞지 않는 불필요한 데이터가 있거나, 데이터가 없는 열들이 포함됨



### series 와 dataframe

* 데이터를 다루기 위해 데이터 프레임(Dataframe)과 시리즈(Series) 제공
* 시리즈(Series)는 1차원 데이터이고, 데이터프레임(Dataframe)은 테이블형(2차원) 데이터이다



### pandas 데이터 타입

* pandas 데이터 타입은 파이썬과 다름
  * object 는 파이썬 의 str 또는 혼용 데이터 타입(문자열)
  * int64 는 파이썬의 int(정수)
  * float64 는 파이썬의 float(부동소수점)
  * bool 는 파이썬의 bool(True 또는 False 값을 가지는 boolean)
  * 이외에 datetime64(날짜/시간), timedelta[ns] (두 datatime64 간의 차) 도 활용됨
* 데이터 타입 변경
  * Series.astype(변경할 타입)



### 데이터프레임(Dataframe) 이해하기

* 데이터프레임은 테이블형(2차원) 데이터이며, 데이터 분석/머신 러닝에서 데이터 처리를 위해 주로 사용함
* 2차원이기 때문에 엑셀/csv 와 같이 데이터가 row, column로 구성되며, 인덱스도 두개, row/column 각각 존재함
  * 행의 레이블은 인덱스로, 열의 레이블은 컬럼으로 부름



### 데이터프레임 데이터 접근하기

* 데이터프레임.loc : index를 통해서 값을 찾음
* 데이터프레임.iloc : 인덱스 변호를 통해서 값을 찾음(0부터 시작)



### 탐색적 데이터 분석

* EDA(Exploratory Data Analysis) 라고 함

* 데이터 분석을 위해 raw data를 다양한 각도에서 관찰하여, 데이터를 이해하는 과정

  * 데이터 분석 주제마다 EDA를 통해 진행하는 과정을 각양각색이므로, 정형화된 패턴은 없지만, 크게 3가지 과정을 기본이다.

  1. 데이터의 출처와 주제에 대한 이해
  2. 데이터의 크기 확인
  3. 데이터 구성 요소의 속성 확인


























