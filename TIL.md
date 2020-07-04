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



### CSV 파일 읽기

```python
data_file = open('00_data/USvideo.csv', 'r', encoding='utf-8-sig')
data_lines = csv.reader(data_file, delimiter=',')
data_file.close()
```

* delimiter = 데이터 구분자 : csv 파일 내에 데이터 구분자를 명시할 수 있음(옵션)



### csv 파일 쓰기

```python
import csv
data_file = open('00_data/tmp_csv.csv', 'w', encoding='utf-8-sig', newline='')
data_write = csv.writer(data_file, delimiter=',')
data_write.writerow(['1', '2', '3'])
data_file.close()
```

* open() 함수에 newline='' 를 넣어주는 이유는 윈도우의 경우에만 csv 모듈에서 데이터를 쓸 때 각 라인 뒤에 빈 라인이 추가되는 문제가 있기 때문이다.

* csv.reader 대신, csv.writer 함수 사용
* writerow 함수에 리스트 형식으로 데이터를 넣으면, 한 라인씩 파일에 추가 됨



### csv 파일 쓰기 다른 기법 (사전 타입으로 파일 쓰기)

```python
import csv

with open('00_data/tmp_csv.csv', 'w', encoding='utf-8-sig', newline='') as writer_csv:
    field_name_list =['First Name', 'Last Name']  # 필드명 정의
    writer = csv.DictWriter(writer_csv, fieldnames=field_name_list)  # 필드명을 미리 선언할 수 있음
    writer.writeheader()  # 보통 csv 파일 상단에는 필드명을 넣기 때문에, 선언된 필드명을 writerheader() 함수로 넣을 수 있음
    writer.writerow({'First Name': 'Dave', 'Last Name': 'Lee'})  # 각 데이터는 사전 타입으로 저장 가능
    writer.writerow({'First Name': 'David', 'Last Name': 'Kim'})
    writer.writerow({'First Name': 'Robin', 'Last Name': 'Park'})
```

* csv.writer 함수 대신에, csv.DictWriter 함수 사용



### XML

* XML(Extensible Markup Language)
  * 특정 목적에 따라 데이터를 태그로 감싸서 마크업하는 범용적인 포멧
  * 마크업 언어는 태그 등을 이용하여 데이터의 구조를 기술하는 언어의 한 가지
  * 가장 친숙한 마크업언어가 HTML
  * ex) <태그 속성="속성값">내용</태그>



### XML 파일 읽고 데이터 추출하기

```python
data_file = open('users.xml', 'r', encoding='utf-8-sig')
soup = BeautifulSoup(data_file, 'xml')
users = soup.select('user')
for user in users:
    print(user.text)
```

1. open() 함수로 xml 데이터 읽기
2. xml 데이터 파싱하기
3. select() 로 원하는 데이터 태그 선택하기
   * 리턴값은 리스트 타입
   * 원하는 데이터가 하나일 경우에는 select_one() 함수 사용
   * 실제 데이터는 각 아이템.text로 추출가능



### API를 이용하여 XML파일 불러오고 원하는 데이터 추출

```python
import requests
from bs4 import BeautifulSoup

keyword = '스마트폰'
google_related_keyword_api = 'http://suggestqueries.google.com/complete/search?output=toolbar&q=' + keyword
response = requests.get(google_related_keyword_api)       # 파일이 아니라, 데이터를 Open API 에서 가져오기 위한 함수
soup = BeautifulSoup(response.content, 'xml')             # requests.get() 의 리턴값은 객체
                                                          # 객체.content 에 가져온 데이터가 있음

datas1 = soup.select('suggestion')

for item in datas1:
    print(item['data'])
```



### JSON 데이터 포멧 이해하기

* JavaScript Object Notation 줄임말
* JSON은 서버와 클라이언트 또는 컴퓨터/프로그램 사이에데이터를 주고 받을 때 사용하는 데이터 포멧
* 키와 값을 괄호와 세미콜론과 같이 간단한 기호로 구성하여 표현할 수 있고, 언어나 운영체제에 구애받지 않기 때문에 많이 사용됨
* 특히 웹/앱 환경에서 Rest API를 사용하여, 서버와 클라이언트 사이에 데이터를 주고 받을때 많이 사용
* JSON 포멧 예
  * {"id":"01", "language":"Java", "edition": "third", "author":"Herbert Schildt"}



### JSON 데이터 포멧 읽기

```python
import json

# 변수에 문자열로 된 JSON 포멧의 데이터가 있을 경우
data = '{ "id":"01", "language": "Java", "edition": "third", "author": "Herbert Schildt" }' 

jsondata = json.loads(data)
print (jsondata['id'], jsondata['language'], jsondata['edition'], jsondata['author'], type(jsondata))
```

* 반대로 json.dumps() 함수로 파이썬 딕셔너리 데이터를 JSON 문자열 데이터로 변환할 수 있음





