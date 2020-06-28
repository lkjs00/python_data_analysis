##  인프런 - 처음하는 파이썬 데이터 분석

### 목표 : 파이썬 데이터 분석 기본 기술 익히기

* 파이썬 데이터 전처리, 데이터 분석, 데이터 시각화



### anaconda

anaconda란?

* 파이썬 기본(컴파일러), 주요 라이브러리, 주요 툴을 모아놓은 패키지
* 파이썬의 장점 : 라이브러리
  * pip install library-name

> 컴파일러 : 프로그래밍 언어로 씌어 있는 코드를 컴퓨터가 실행할 수 있는 코드로 변환하는 프로그램



### jupyter notebook 란?

* Editor vs jupytor notebook
  * 한줄 한줄 코드 실행 결과 확인이 쉽다.
  * 문서와 코드를 함께 작성/저장 할 수 있다.



### 변수(variable)

> 데이터를 기반으로, 컴퓨터에 명령을 내리는 것: 문자 또는 숫자

* 문자열(string), 숫자:정수(integer), 숫자:부동소수점(float), 특별한 타입:True/False(Boolean)



### 라이브러리 설치하기

```python
import pandas
```



### 파일 오픈

```python
data_file = open('00_data/text_data.txt', 'r', encoding='utf-8-sig')
```

* 절대 경로
  * 최초의 시작점에서 경유한 경로를 전부 기입하는 방식
* 상대 경로
  * 파일을 찾는 위치부터 상대적인 경로를 기입하는 방식
* 파일 열기 모드
  * `r` : 읽기 모드 - 파일을 읽기만 할 때 사용함
  * `w` :  쓰기 모드 - 파일에 데이터를 쓸 때 사용함(기존 파일 데이터는 삭제됨)
  * `a` : 추가 모드 - 파일의 기존 데이터 끝에서부터 데이터를 추가할 때 사용함



###  파일 읽기

* readlines() 함수를 호출해서, 전체 데이터를 한줄씩 리스트타입으로 읽어올 수 있음.

```python
data_file = open('00_data/text_data.txt', 'r', encoding='utf-8-sig')
data_lines = data_file.readlines()
```

* readline() 함수를 호출해서, 현재까지 읽은 파일 데이터의 다음 한 줄을 문자열 타입으로 읽을 수 있음.

```python
data_file = open('00_data/text_data.txt', 'r', encoding='utf-8-sig')
data_line = data_file.readline()
print (data_line)
```

* read() 함수를 호출해서, 전체 파일 데이터를 호출해서, 전체 파일 데이터를 문자열 타입으로 읽을 수 있음.

```python
data_file = open('00_data/text_data.txt', 'r', encoding='utf-8-sig')
data = data_file.read()
```

























