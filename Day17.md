# Day17 🍕



## 파이썬 기초 복습



### 1. 판다스 자료 구조

- 판다스는 시리즈(Series)와 데이터프레임(DataFrame)이라는 데이터 형식을 제공
- Numpy : 배열 및 연산
- pandas : 자료구조 및 시각화



#### 1) 시리즈

- 데이터가 순차적으로 나열된 **1차원 배열(열벡터)**
- **인덱스(index)**는 **데이터 값(value)**과 일대일 대응
  - 시리즈의 인덱스는 데이터 값의 위치를 나타내는 이름표(주소) 역할
- `pandas.Series(딕셔너리 객체) `: 딕셔너리 -> 시리즈 변환

```python
# 판다스 import
import pandas as pd

# key:value 를 쌍으로 갖는 딕셔너리를 생성, 변수 dict_data에 저장
dict_data = {'a' : 1, 'b' : 2, 'c' : 3}

# 판다스 Series() 함수로 딕셔너리를 시리즈로 변환, 변수 sr에 저장
sr = pd.Series(dict_data)
```



#### 2) 데이터프레임

- **2차원 배열**

- 여러 개의 열벡터(시리즈)들이 같은 행 인덱스를 기준으로 결합된 2차원 벡터 또는 행렬(matrix)

- 행과 열을 나타내기 위해서 **행 인덱스와 열 이름** 두가지 종류의 주소를 사용

  - 열은 공통의 속성을 갖는 일련의 데이터의 집합
  - 행은 공통적이고 다양한 속성 데이터들의 모음인 레코드(record)

  

##### (1) 데이터프레임 만들기

- `pandas.DataFrame(딕셔너리 객체)` : 딕셔너리 -> 데이터프레임 변환

```python
import pandas as pd

# key:value 를 쌍으로 갖는 딕셔너리를 생성, 변수 dict_data에 저장
dict_data = {'c0' : [1, 2, 3], 'c1' : [4, 5, 6], 'c2' : [7, 8, 9], 'c3' : [10, 11, 12], 'c4' : [13, 14, 15]}

# 판다스 DataFrame() 함수로 딕셔너리를 데이터프레임으로 변환, 변수 df에 저장
df = pd.DataFrame(dict_data)
```

- `pandas.DataFrame(2차원 배열, index, columns)`: 행 인덱스, 열 이름 직접 지정

```python
import pandas as pd

# 행 인덱스 / 열 이름을 지정하여 데이터프레임 만들기
df = pd.DataFrame([[22, '남', '인천대'], [21, '여', '경기대'], [20, '남', '부산대']],
                  index=['규석', '영신', '성민'],
                  columns=['나이', '성별', '학교'])
```



##### (2) 행 / 열 이름 변경

- 행 인덱스 변경: `DataFrame객체.rename(index={'기존 인덱스':'새 인덱스', ...})`
- 열 이름 변경: `DataFrame객체.rename(columns={'기존 열 이름':'새 열 이름', ...})`

- `inplace = True 옵션`: 기존 객체에 반영



##### (3) 행 / 열 삭제

- 행 삭제: `DataFrame객체.drop('행 인덱스' 또는 배열, axis=0)`

- 열 삭제: `DataFrame객체.drop('열 이름' 또는 배열, axis=1)`

- `axis`는 축 옵션



##### (4) 행 선택

- `DataFrame객체.loc['행 인덱스']`: 인덱스 이름을 기준으로 행을 선택
  - 범위 지정 시 **범위 끝 포함**
- `DataFrame객체.iloc[위치 인덱스]`: 정수형 위치 인덱스를 기준으로 행을 선택
  - 범위 지정 시 **범위 끝 미포함**

```python
import pandas as pd

exam_data = {'국어' : [70, 90, 80], '수학' : [90, 85, 80], '영어' : [100, 80, 90], '음악' : [70, 90, 100]}
df = pd.DataFrame(exam_data, index=['인서', '연정', '린하'])

# 행 인덱스 이름을 사용하여 행 선택
label1 = df.loc['인서']
label2 = df.loc[['인서', '린하']]
label3 = df.loc['인서':'연정']

# 정수형 위치 인덱스를 사용하여 행 선택
position1 = df.iloc[0]
position2 = df.iloc[[1,2]]
position3 = df.iloc[0:1]
```



##### (5) 열 선택

- `DataFrame객체['열 이름']`
- `DataFrame객체.열이름`
- 열은 정수형 위치 인덱스라는 개념이 존재 X

```python
import pandas as pd

exam_data = {'국어' : [70, 90, 80], '수학' : [90, 85, 80], '영어' : [100, 80, 90], '음악' : [70, 90, 100]}
df = pd.DataFrame(exam_data, index=['요셉', '성훈', '동호'])

# '수학' 점수 데이터만 선택(열 선택)
math = df['수학']

# '영어' 점수 데이터만 선택(열 선택)
english = df.영어

# 열 두 개 선택
kor_music = df[['국어', '음악']]
```



##### (6) 원소 선택

- 데이터프레임의 행 인덱스와 열 이름을 [행, 열] 형식의 **2차원 좌표**로 입력하여 원소 위치를 지정

- `DataFrame객체.loc[행 인덱스 이름, 열 이름]`
- `DataFrame객체.iloc[행 번호, 열 번호]`

```python
import pandas as pd

exam_data = {'이름' : ['용준', '수빈', '재영'],
             '국어' : [70, 90, 80],
             '수학' : [90, 85, 80], 
             '영어' : [100, 80, 90], 
             '음악' : [70, 90, 100]}
df = pd.DataFrame(exam_data)

# 데이터프레임 df의 특정 원소 1개 선택('용준'의 '영어' 점수)
a = df.loc['용준', '영어']
b = df.iloc[0, 2]

# 데이터프레임 df의 특정 원소 2개 선택('수빈'의 '국어', '수학' 점수)
c = df.loc['수빈', ['국어', '수학']]
d = df.iloc[1, [0, 1]]
e = df.loc['수빈', '국어':'수학']
f = df.iloc[1, 0:2]

# 데이터프레임 df의 2개 이상의 행과 열에 속하는 원소들 선택('수빈', '재영'의 '영어', '음악' 점수)
g = df.loc[['수빈', '재영'], ['영어', '음악']]
h = df.iloc[[1, 2], [2, 3]]
i = df.loc['수빈':'재영', '영어':'음악']
j = df.iloc[1:, 2:]
```



##### (7) 행 / 열 추가

- 행 추가: `DataFrame객체.loc['새로운 행 이름'] = 데이터 값`
- 열 추가: `DataFrame객체['새로운 열 이름'] = 데이터 값`

```python
import pandas as pd

exam_data = {'이름' : ['건국', '예진', '원준'],
             '국어' : [70, 90, 80],
             '수학' : [90, 85, 80], 
             '영어' : [100, 80, 90], 
             '음악' : [70, 90, 100]}
df = pd.DataFrame(exam_data)

# '체육' 점수 열(column) 추가
df['체육'] = [80, 70, 75]

# 새로운 행(row) 추가 - 3번 행에 같은 원소 값 입력
df.loc[3] = 0

# 새로운 행(row) 추가 - 4번 행에 원소 값 여러 개의 배열 입력
df.loc[4] = ['한결', 100, 75, 85, 80]

# 새로운 행(row) 추가 - 기존 행 복사
df.loc[5] = df.loc[3]
```

- 열을 중간에 추가: `DataFrame객체.insert(원하는 컬럼 위치, 새로운 컬럼 이름, 데이터 값)`
  - 위치는 0부터 시작

```python
# '체육' 점수 열을 3번째 위치에 추가
df.insert(3, '체육', df['국어'] + df['수학'])
```



##### (8) 원소 값 변경

- `DataFrame객체 원소 선택 = 새로운 값`

```python
import pandas as pd

exam_data = {'이름' : ['예진', '지우', '진석'],
             '국어' : [70, 90, 80],
             '수학' : [90, 85, 80], 
             '영어' : [100, 80, 90], 
             '음악' : [70, 90, 100]}
df = pd.DataFrame(exam_data)

# 데이터프레임 df의 특정 원소를 변경('예진'의 '음악' 점수)
df.loc['예진', '음악'] = 85
df.loc['예진']['음악'] = 100
df.iloc[0, 3] = 80
df.iloc[0][3] = 90

# 데이터프레임 df의 원소 여러 개 변경('지우'의 '수학', '영어' 점수)
df.loc['지우', ['수학', '영어']] = 100
df.loc['지우', ['수학', '영어']] = 100, 95
```



##### (9) 행, 열 위치 바꾸기

- `DataFrame객체.transpose()`
- `DataFrame객체.T`



##### (10) 행 인덱스

- `DataFrame객체.set_index('열 이름', inplace = True)`: 특정 열을 행 인덱스로 설정
- `DataFrame객체.reset_index()`: 행 인덱스 초기화
- `DataFrame객체.index.name = '행 인덱스 이름'` : 행 인덱스의 이름 지정
- `DataFrame객체.index.rename('바꿀 이름', inplace = True)`: 행 인덱스의 이름을 바꿀 경우 



##### (11) 행 인덱스 / 열 순서 변경

- 새로운 배열로 행 인덱스 재지정: `DataFrame객체.reindex([변수 배열])`
- 새로운 배열로 열 순서 변경: `DataFrame객체.reindex(columns = [변수 배열])`

```python
import pandas as pd

dict_data = {'c0' : [1, 2, 3], 'c1' : [4, 5, 6], 'c2' : [7, 8, 9], 'c3' : [10, 11, 12], 'c4' : [13, 14, 15]}

# 'r0', 'r1', 'r2'이 행 인덱스인 데이터프레임으로 변환
df = pd.DataFrame(dict_data, index = ['r0', 'r1', 'r2'])

# 행 인덱스 재배열로 사용될 변수를 지정
new_index = ['r0', 'r1']

# 행 인덱스를 ['r0', 'r1']로 재지정
ndf = df.reindex(new_index)

# 열 순서 변경
ndf4 = ndf3.reindex(columns = ['c1', 'c0', 'c2', 'c3', 'c4'])
```



##### (12) 데이터프레임 정렬

- 행 인덱스를 기준으로 정렬: `DataFrame객체.sort_index()`
- 특정 열의 데이터 값을 기준으로 정렬: `DataFrame객체.sort_values()`
- `ascending 옵션`을 사용하여 오름차순 혹은 내림차순으로 설정
  - True : 오름차순 정렬 (기본값)
  - False : 내림차순 정렬

```python
import pandas as pd

dict_data = {'c0' : [1, 2, 3], 'c1' : [6, 4, 5], 'c2' : [7, 8, 9], 'c3' : [10, 11, 12], 'c4' : [13, 14, 15]}

df = pd.DataFrame(dict_data, index = ['r0', 'r1', 'r2'])

# 내림차순으로 행 인덱스 정렬
ndf = df.sort_index(ascending=False)

# 오름차순으로 행 인덱스 정렬
ndf2 = ndf.sort_index()  # ascending = True

# c1 열을 기준으로 내림차순 정렬
ndf3 = df.sort_values(by='c1', ascending = False)

# c1 열을 기준으로 오름차순 정렬
ndf4 = df.sort_values(by='c1', ascending = True)
```



---



### 2. 외부파일 읽어오기

- 판다스는 다양한 형태의 외부 파일을 읽어와 데이터프레임으로 변환하는 함수를 제공

- 어떤 파일이든 판다스 객체인 데이터프레임으로 변환되면 판다스의 모든 함수와 기능을 자유롭게 사용 가능

- 데이터 프레임을 다양한 유형의 파일로 저장 가능

  - CSV, JSON, HTML, MS Excel, SQL, ...

  

#### 1) CSV 파일

- comma-separated values 의 약자
  - 데이터 값을 쉼표(,)로 구분하고 있다는 의미를 가진 파일
- CSV 파일 -> 데이터프레임
  `pandas.read_csv("파일 경로(이름).csv")`

```PYTHON
import pandas as pd

# 파일 경로를 찾고, 변수 file_path에 저장
file_path = './read_test.csv'

# CSV파일 읽어오기
df1 = pd.read_csv(file_path)
df2 = pd.read_csv(file_path, header = None)
df4 = pd.read_csv(file_path, index_col = 'c0')
```



#### 2) Excel 파일

- Excel 파일(확장자 .xlsx)의 행과 열은 데이터프레임의 행, 열로 일대일 대응
- Excel 파일 -> 데이터프레임
  `pandas.read_excel("파일 경로/이름.xlsx")`



#### 3) jSON 파일

- JSON 파일(확장자 .json)은 데이터 공유 목적으로 개발된 특수한 파일 형식
- 파이썬 딕셔너리와 비슷하게 'key:value' 구조를 가짐
  `pandas.read_json("파일 경로/이름.json")`



---



### 3. 산술연산

#### 1) 판다스 객체의 산술 연산 3단계 프로세스(내부)

1. 행/열 인덱스를 기준으로 모든 원소를 정렬
2. 일대일 대응되는 원소끼리 연산
3. 대응되는 원소가 없다면 NaN



#### 2) NaN 처리하기

- 어느 한 쪽에 원소가 존재하지 않거나 NaN이면 연산 결과로 NaN 처리됨

##### (1) 시리즈

- `fill_value 옵션`

- 연산 결과가 NaN으로 반환되지 않도록 하기 위한 연산 메소드
- ex) `sr_add = sr1.add(sr2, fill_value=0)`



##### (2) 데이터프레임

-  `DataFrame객체.ffill(inplace = True)`
  - 이전 연산에 대한 결과값을 NaN 대신 출력
- `DataFrame객체.fillna(0, inplace = True)`
  - NaN을 0으로 바꾸고 계산