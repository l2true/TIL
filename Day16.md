# 16일차 🍕



## Matplotlib 그래프 심화



### 1. 설명을 덧붙이는 주석

- `annotate()` 함수: 화살표와 텍스트 위치를 잡아서 배치
    - 위치를 나타내는 (x,y) 좌표에서 x값은 인덱스 번호 사용
    - y값: 실제 y값 (예제: 인구수 데이터 숫자값)
    - `rotation 옵션`: 양의 회전 방향은 반시계 방향
    - `va/ha `옵션: 텍스트 정렬 (상하/좌우)
- `arrowprops 옵션`: 화살표 주석 
    - 화살표 스타일, 시작점과 끝점의 좌표를 입력
- 예제에서는 주석을 넣을 여백 공간을 확보하기 위해 `ylim()` 함수를 사용하여 y축의 범위 증가

```python
# y축 범위 지정 (최소값, 최대값)
plt.ylim(50000, 800000)

# 주석 표시 - 화살표
plt.annotate('', 
             xy=(20, 620000),    # 화살표의 머리 부분(끝점)
             xytext=(2, 290000), # 화살표의 꼬리 부분(시작점)
             xycoords='data',    # 좌표체계 
             # 화살표 서식
             # dict : 화살표의 특성을 지정
             # lw : 화살표의 두께
             arrowprops=dict(arrowstyle='->', color='skyblue', lw=5)
            )

plt.annotate('', 
             xy=(44, 450000),    # 화살표의 머리 부분(끝점)
             xytext=(30, 600000), # 화살표의 꼬리 부분(시작점)
             xycoords='data',    # 좌표체계 
             # 화살표 서식
             # dict : 화살표의 특성을 지정
             # lw : 화살표의 두께
             arrowprops=dict(arrowstyle='->', color='skyblue', lw=5)
            )

# 주석 표시 - 텍스트
plt.annotate('인구이동 증가(1970-1995)',  # 텍스트 입력 
             xy=(10, 500000),             # 텍스트 위치 기준점(중간)
             rotation=24,                 # 텍스트 회전 각도
             va='center',                 # 텍스트 상하 정렬('center', 'top', 'bottom')
             ha='center',                 # 텍스트 좌우 정렬('center', 'left', 'right'),
             fontsize=15
            )

plt.annotate('인구이동 감소(1995-2017)',  # 텍스트 입력 
             xy=(37, 580000),             # 텍스트 위치 기준점(중간)
             rotation=-13,                 # 텍스트 회전 각도
             va='center',                 # 텍스트 상하 정렬('center', 'top', 'bottom')
             ha='center',                 # 텍스트 좌우 정렬('center', 'left', 'right'),
             fontsize=15
            )
```

![image](https://user-images.githubusercontent.com/100326309/156531192-c082af00-946a-44e7-a69c-79ac1907e647.png)



### 2. axe 객체

#### 1) 화면을 분할하여 그래프 여러 개 그리기 

여러 개의 axe 객체를 생성, 분할된 화면마다 axe 객체를 하나씩 배정

- axe 객체는 각각 서로 다른 그래프 표현 가능
- 한 화면에서 여러 개의 그래프를 비교하거나 다양한 정보를 동시에 보여줄 때 사용

- `figure()`: 그래프를 그리는 그림틀 생성

  - `figsize 옵션`: (가로, 세로) 그림틀 크기 지정

- `add_subplot(행의 개수, 열의 개수, 서브플롯 순서)` : 그림틀을 여러 개로 분할

  - ex) `ax1 = fig.add_subplot(2, 1, 1)`

- `plot(x,y)`: axe 객체에 그래프 그리기

  - marker : 마커의 모양('o', '+', '*', '.')

  - markerfacecolor : 마커의 배경색

  - markersize : 마커의 크기

  - color: 선의 색

  - linewidth: 선의 두께

  - label: 범례 지정

- 예제에서는 점으로만 구성된 그래프와 점, 선으로 구성된 그래프 두 개 생성

```python
# 그래프 객체 생성
fig  = plt.figure(figsize = (10,10))
ax1 = fig.add_subplot(2,1,1)
ax2 = fig.add_subplot(2,1,2)

# axe 객체에 plot 함수로 그래프 출력
ax1.plot(dt_g, 'o', markersize = 10)
ax2.plot(dt_g, marker = 'o', markerfacecolor = 'green', markersize = 10,
        color = 'olive', linewidth = 2, label = '서울->경기')
ax2.legend(loc = 'best') # 범례 위치

plot.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531261-b36c814f-9984-41a2-8696-da452f37ad8d.png)



#### 2) axe 객체 그래프에 제목, 축 이름 추가

- `set_title()` : 제목 추가
- `set_xlabel()`: x축 이름 지정
- `set_ylable()`: y축 이름 지정
- `set_xticklabels`: 축 눈금 라벨 회전
- `tick_params()`: 축 눈금 라벨의 크기

```python
# 차트 제목 추가
ax.set_title('서울 -> 경기 인구 이동', size = 20)

# 축 이름 추가
ax.set_xlabel('기간', size = 12)
ax.set_ylabel('이동 인구 수', size = 12)

# 축 눈금 라벨 회전
ax.set_xticklabels(dt_g.index, rotation = 90)

# 축 눈금 라벨 크기
ax.tick_params(axis = "x", labelsize = 10)
ax.tick_params(axis = "y", labelsize = 10)
```

![image](https://user-images.githubusercontent.com/100326309/156531289-3a146fdd-dc79-4fd3-9e0e-a7e6ccc9bb46.png)



#### 3) 한 화면에 여러 개의 그래프 그리기

- 서울특별시에서 충청북도, 전라남도, 경상북도로 이동한 인구 변화 그래프 3개를 하나의 화면에 출력
- 그래프 객체 1개 생성: `add_subplot(1, 1, 1)`
- 각 지역에 해당하는 행 데이터 선택, 선 그래프를 출력하는 `plot()`메소드를 3번 적용

```python
import pandas as pd

# 데이터 시각화에 사용할 matplotlib.pyplot 모듈을 import
import matplotlib.pyplot as plt

# matplotlib 한글 폰트 오류 문제 해결
from matplotlib import font_manager, rc
## font_manager는 경로와 이름을 가지고 폰트를 지정
font_path = "./malgun.ttf"
font_name = font_manager.FontProperties(fname=font_path).get_name()
## rc는 폰트를 적용
rc('font', family=font_name)

# Excel 데이터를 데이터프레임 변환 (첫 열을 헤더로 사용)
df = pd.read_excel("./시도별 전출입 인구수.xlsx", header = 0)

# 누락값(NaN)을 앞 데이터로 채움(엑셀 양식 병합)
df = df.fillna(method='ffill')

# 서울에서 다른 지역으로 이동한 데이터만 추출
mask = (df['전출지별'] == '서울특별시') & (df['전입지별'] != '서울특별시')
df_seoul = df[mask]

# '전출지별' 열은 필요 없으므로 삭제
df_seoul = df_seoul.drop(['전출지별'], axis=1)

# '전입지별' 열은 '전입지'로 이름 변경 후 행인덱스로 설정
df_seoul.rename({'전입지별': '전입지'}, axis=1, inplace=True)
df_seoul.set_index('전입지', inplace=True)

# 서울에서 '충청북도', '전라남도', '경상북도'로 이동한 인구 데이터 값만 선택
col_years = list(map(str, range(1970, 2018)))
df_3 = df_seoul.loc[['충청북도', '전라남도', '경상북도'], col_years]

# 스타일 서식 지정
plt.style.use('ggplot')

# 그래프 객체 생성
fig = plt.figure(figsize=(20, 5))
ax = fig.add_subplot(1, 1, 1)

# axe 객체에 plot() 함수로 그래프 출력
ax.plot(col_years, df_3.loc['충청북도', :], marker='o', markerfacecolor='green',
        markersize=10, color='olive', linewidth=2, label='서울 -> 충북')
ax.plot(col_years, df_3.loc['전라남도', :], marker='o', markerfacecolor='blue',
        markersize=10, color='skyblue', linewidth=2, label='서울 -> 전남')
ax.plot(col_years, df_3.loc['경상북도', :], marker='o', markerfacecolor='red',
        markersize=10, color='magenta', linewidth=2, label='서울 -> 경북')

ax.legend(loc='best')

# 차트 제목 추가
ax.set_title('서울 -> 충북, 전남, 경북 인구 이동', size=20)

# 축 이름 추가
ax.set_xlabel('기간', size=12)
ax.set_ylabel('이동 인구수', size=12)

# 축 눈금 라벨을 회전
ax.set_xticklabels(col_years, rotation=90)

# 축 눈금 라벨 크기
ax.tick_params(axis="x", labelsize=10)
ax.tick_params(axis="y", labelsize=10)

plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531319-45b2cb79-206b-431f-969c-61b1e231259a.png)



#### 4) 여러 화면에 여러 개의 그래프 그리기

- axe 객체 4개 생성: `ax1 = fig.add_subplot(2, 2, 1~4)` -> 2행 2열
- 그래프 4개 출력: `ax1.plot(col_years, df_4.loc['충청북도', :]` -> y값 각각에 맞는 데이터 선택
- 그래프 디자인 모두 따로 코드 작성 (or for 반복문)

```python
# 서울에서 '충청북도', '전라남도', '경상북도, 강원도'로 이동한 인구 데이터 값만 선택
col_years = list(map(str, range(1970, 2018)))
df_4 = df_seoul.loc[['충청북도', '전라남도', '경상북도', '강원도'], col_years]

# 스타일 서식 지정
plt.style.use('ggplot')

# 그래프 객체 생성
fig = plt.figure(figsize=(20, 20))
ax1 = fig.add_subplot(2, 2, 1)
ax2 = fig.add_subplot(2, 2, 2)
ax3 = fig.add_subplot(2, 2, 3)
ax4 = fig.add_subplot(2, 2, 4)

# axe 객체에 plot() 함수로 그래프 출력
ax1.plot(col_years, df_4.loc['충청북도', :], marker='o', markerfacecolor='green',
        markersize=10, color='olive', linewidth=2, label='서울 -> 충북')
ax2.plot(col_years, df_4.loc['전라남도', :], marker='o', markerfacecolor='blue',
        markersize=10, color='skyblue', linewidth=2, label='서울 -> 전남')
ax3.plot(col_years, df_4.loc['경상북도', :], marker='o', markerfacecolor='red',
        markersize=10, color='magenta', linewidth=2, label='서울 -> 경북')
ax4.plot(col_years, df_4.loc['강원도', :], marker='o', markerfacecolor='red',
        markersize=10, color='yellow', linewidth=2, label='서울 -> 강원')

ax1.legend(loc='best')
ax2.legend(loc='best')
ax3.legend(loc='best')
ax4.legend(loc='best')

# 차트 제목 추가
ax1.set_title('서울 -> 충북 인구 이동', size=20)
ax2.set_title('서울 -> 전남 인구 이동', size=20)
ax3.set_title('서울 -> 경북 인구 이동', size=20)
ax4.set_title('서울 -> 강원 인구 이동', size=20)

# 축 이름 추가
ax1.set_xlabel('기간', size=12)
ax1.set_ylabel('이동 인구수', size=12)
ax2.set_xlabel('기간', size=12)
ax2.set_ylabel('이동 인구수', size=12)
ax3.set_xlabel('기간', size=12)
ax3.set_ylabel('이동 인구수', size=12)
ax4.set_xlabel('기간', size=12)
ax4.set_ylabel('이동 인구수', size=12)

# 축 눈금 라벨을 회전
ax1.set_xticklabels(col_years, rotation=90)
ax2.set_xticklabels(col_years, rotation=90)
ax3.set_xticklabels(col_years, rotation=90)
ax4.set_xticklabels(col_years, rotation=90)

# 축 눈금 라벨 크기
ax1.tick_params(axis="x", labelsize=10)
ax1.tick_params(axis="y", labelsize=10)
ax2.tick_params(axis="x", labelsize=10)
ax2.tick_params(axis="y", labelsize=10)
ax3.tick_params(axis="x", labelsize=10)
ax3.tick_params(axis="y", labelsize=10)
ax4.tick_params(axis="x", labelsize=10)
ax4.tick_params(axis="y", labelsize=10)

''''
#for 반복문
for i in range(0,4):
    ax[i].set_xlabel('기간', size=12)
    ax[i].set_ylabel('이동 인구수', size=12)
    ax[i].legend(loc='best')
    ax[i].set_xticklabels(dt_g.index, rotation=90)
    ax[i].tick_params(axis="x", labelsize=10)
    ax[i].tick_params(axis="y", labelsize=10)
''''
fig.tight_layout()

plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531353-d853da8f-cd9d-480d-a4fd-2f56357ece4e.png)



#### 5) 그래프 간격 조정

- 자동조정: `tight_layout()` 
  - ex) `fig.tight_layout()`

- 직접 조정: `subplots_adjust()`

  - ex) `plt.subplts_adjust()`

  - left, right, top, bottom, wspace(서브 플롯 사이의 좌우 예비 공간), hspace(서브 플롯 사이의 상하 예비 공간)



### 3. Matplotlib에서 사용할 수 있는 색상 확인하기

``` python
import matplotlib

# 컬러 정보를 받아올 변수
colors = {}

for name, hex in matplotlib.colors.cnames.items():
    colors[name] = hex
    
print(colors)
```

---



## 면적 그래프 (area plot)

- `plot(kind = 'area')`
- 각 열의 데이터를 선 그래프로 구현, 선 그래프와 x축 사이의 공간에 색 적용

- 색의 투명도 지정: 기본값: 0.5, 범위: 0~1
- `stacked 옵션`: 그래프 누적 여부 설정 (기본값: `stacked = True`)
  - 각 열의 선 그래프를 다른 열의 선 그래프 위로 쌓아올리는 방식
  - 각 열의 패턴과 열 전체의 합계가 어떻게 변하는지 확인

```python
import pandas as pd

# 데이터 시각화에 사용할 matplotlib.pyplot 모듈을 import
import matplotlib.pyplot as plt

# matplotlib 한글 폰트 오류 문제 해결
from matplotlib import font_manager, rc
## font_manager는 경로와 이름을 가지고 폰트를 지정
font_path = "./malgun.ttf"
font_name = font_manager.FontProperties(fname=font_path).get_name()
## rc는 폰트를 적용
rc('font', family=font_name)

# Excel 데이터를 데이터프레임 변환 (첫 열을 헤더로 사용)
df = pd.read_excel("./시도별 전출입 인구수.xlsx", header = 0)

# 누락값(NaN)을 앞 데이터로 채움(엑셀 양식 병합)
df = df.fillna(method='ffill')

# 서울에서 다른 지역으로 이동한 데이터만 추출
mask = (df['전출지별'] == '서울특별시') & (df['전입지별'] != '서울특별시')
df_seoul = df[mask]

# '전출지별' 열은 필요 없으므로 삭제
df_seoul = df_seoul.drop(['전출지별'], axis=1)

# '전입지별' 열은 '전입지'로 이름 변경 후 행인덱스로 설정
df_seoul.rename({'전입지별': '전입지'}, axis=1, inplace=True)
df_seoul.set_index('전입지', inplace=True)

# 서울에서 '충청북도', '전라남도', '경상북도'로 이동한 인구 데이터 값만 선택
col_years = list(map(str, range(1970, 2018)))
df_4 = df_seoul.loc[['충청북도', '전라남도', '경상북도', '강원도'], col_years]
df_4 = df_4.T

# 스타일 서식 지정
plt.style.use('ggplot')

# 데이터프레임 인덱스를 정수형 변경
df_4.index = df_4.index.map(int)

# 면적 그래프 그리기 (누적x)
df_4.plot(kind = 'area', stacked = False, alpha = 0.2, figsize = (20,10))
# (누적o) df_4.plot(kind = 'area', stacked = True, alpha = 0.2, figsize = (20,10))

plt.title('서울 -> 타 시도 인구 이동', size = 30)
plt.xlabel('기간', size = 20)
plt.ylabel('이동 인구 수', size = 20)
plt.legend(loc = 'best', fontsize = 15)

plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531399-85bddd4a-64e5-4e97-bead-e8002019b8ce.png)



## 막대 그래프 (bar plot)

- `plot(kind = 'bar')` / `plot(kind = 'barh')`
- 데이터 값의 크기에 비례하여 높이를 갖는 직사각형 막대로 표현
- 데이터 값의 차이를 효과적으로 설명

```python
# 세로형 막대 그래프 그리기
df_4.plot(kind = 'bar', figsize = (20,10), width = 0.7,
         color = ['orange', 'green', 'red', 'blue'])

# 가로형 막대 그래프 그리기
df_4.plot(kind = 'barh', figsize = (20,10), width = 0.7,
         color = ['orange', 'green', 'red', 'blue'])
```

![image](https://user-images.githubusercontent.com/100326309/156531427-9b044ea8-f76e-4e3b-ac4d-62f02296f3ce.png)

```python
# 합계 그래프 그리기 (가로형)
# 2010-2017년 이동 인구 수를 합계하여 새로운 열로 추가
df_4['합계'] = df_4.sum(axis = 1)

# 가장 큰 값부터 정렬
df_total = df_4[['합계']].sort_values(by = '합계', ascending = True)

# 그래프 그리기
df_total.plot(kind = 'barh', figsize = (10, 3), width = 0.5,
         color = ['skyblue'])
```

![image](https://user-images.githubusercontent.com/100326309/156531468-00e8b964-66c6-48f9-a5f9-3938867cdbca.png)





## 히스토그램 (histogram)

- `plot(kind = 'hist')`

- 변수가 하나인 단변수 데이터의 빈도수를 그래프로 표현
- x축을 같은 크기의 여러 구간으로 나누고, 각 구간에 속하는 데이터 값의 개수(빈도)

```python
import pandas as pd
import matplotlib.pyplot as plt

# 스타일 서식 지정
plt.style.use('bmh')

# df 생성
df = pd.read_csv('./auto-mpg.csv', header = None)

# 열 이름 지정
df.columns = ['mpg', 'cylinders', 'displacement', 'horsepower', 'weight',
            'acceleration', 'model_year', 'origin', 'name']

# 히스토그램 그래프 그리기
df['mpg'].plot(kind = 'hist', bins = 10, color = 'coral', figsize = (10,5))

plt.title('Histogram')
plt.xlabel('mpg')
plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531498-18f9a088-f914-48fe-9131-1a8ab49324c2.png)



## 산점도 (scatter)

- `plot(kind = 'scatter', x, y)`
- 서로 다른 두 변수 사이의 관계를 표현
- 점의 색상(c), 크기(s) 옵션

```python
# 산점도 그래프 그리기
df.plot(kind='scatter', x='weight', y='mpg', 
        c='coral', s=10, figsize=(10, 5))
plt.title('Scatter Plot - mpg vs weight')
plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531534-71ab9e6e-799b-48cf-9589-854e57049343.png)

- 산점도에서 새로운 변수를 추가하여 점의 크기 또는 색상으로 표현 가능
  - 새로운 변수로 실린더 개수('cylinders'열) 추가
  - 실린더 개수를 나타내는 정수를 그대로 쓰되, 해당 열의 최댓값 대비 상대적 크기를 나타내는 비율을 계산하여 `'cylinders_size'`변수에 저장
  - 점의 크기에 변화를 주기 때문에 비눗방울과 비슷하여 **'버블차트'**라고 부름

```python
# cylinders_size 변수 생성
cylinders_size = df.cylinders / df.cylinders.max() * 300

# cylinders_size에 따라 점의 크기가 다른 버블차트 그리기
# alpha : 투명도
df.plot(kind='scatter', x='weight', y='mpg', c='coral', s=cylinders_size, 
        figsize=(10, 5), alpha=0.3) 
plt.title('Scatter Plot - mpg vs weight')
plt.show()

# cylinders_size에 따라 점의 색상이 다른 버블차트 그리기
# marker : 십자(+)로
# cmap: 'viridis' 컬러맵 사용
df.plot(kind='scatter', x='weight', y='mpg', marker='+', c=cylinders_size, 
        cmap='viridis', s=50, figsize=(10, 5), alpha=0.3)
plt.title('Scatter Plot - mpg vs weight')
```

![image](https://user-images.githubusercontent.com/100326309/156531558-91df5f68-217b-4165-9716-48fca605a6e1.png)

![image](https://user-images.githubusercontent.com/100326309/156531590-d41fff4a-d1fe-49d9-a06b-a83a294d3869.png)



## 파이차트 (pie chart)

- `plot(kind = 'pie')`

- 원을 파이 조각처럼 나누어서 표현
  - 데이터 값의 크기에 비례

- 예제

  - 데이터 개수를 세기 위해 숫자 1을 원소로 갖는 'count' 열을 생성

  - `groupby()` 함수를 사용하여 '제조국가'를 3개의 그룹으로 나눔

  - `sum()` 함수를 사용하여 그룹별 개수의 합계를 계산

```python
# 데이터 개수 카운트를 위해 값 1을 원소로 갖는 열을 추가
df['count'] = 1

# origin 열을 기준으로 그룹화, 합계 연산
df_origin = df.groupby('origin').sum()
print(df_origin)

# 제조국가 이름 변경
df_origin.index = ['USA', 'EU', 'JAPAN']

# count 열을 사용하여 파이 차트 만들기
df_origin['count'].plot(kind='pie', figsize=(7, 5), autopct='%0.1f%%',
                        startangle=10, colors=['chocolate', 'bisque', 'cadetblue'])

plt.title('Model Origin', size=20)
plt.axis('equal')
plt.legend(labels=df_origin.index, loc='upper right')

plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531612-a7ddbf21-7379-4501-bae2-c662eaa2c1c4.png)





## 박스플롯 (box plot)

- 제조국가별 연비 분포를 보여주는 박스 플롯 그리기

  - 그림틀을 2개의 axe 객체로 분할하기 위해서 `add_subplot()` 함수 사용
    - 수직 박스 플롯은 `vert=True` 옵션 사용
    - 수평 박스 플롯은 `vert=False` 옵션 사용

  - 각 axe 객체에 박스 플롯을 그리는 `boxplot()` 함수를 사용

```python
# 그래프 객체 생성
fig = plt.figure(figsize = (15,5))
ax1 = fig.add_subplot(1,2,1)
ax2 = fig.add_subplot(1,2,2)

# 박스 플롯 만들기
ax1.boxplot(x=[df[df['origin']==1]['mpg'],
               df[df['origin']==2]['mpg'],
               df[df['origin']==3]['mpg']],
            labels=['USA', 'EU', 'JAPAN'])

# 가로형 박스 플롯 만들기
ax2.boxplot(x=[df[df['origin']==1]['mpg'],
               df[df['origin']==2]['mpg'],
               df[df['origin']==3]['mpg']],
            labels=['USA', 'EU', 'JAPAN'],
            vert=False)

plt.show()          
```

![image](https://user-images.githubusercontent.com/100326309/156531628-d4f4ea09-92aa-42cb-b974-3eeb2a279856.png)





---

- `map()`: 여러 개의 데이터를 한번에 다른 데이터 타입으로 변환
  -  map(변환할 데이터 타입, 데이터)
  - ex) `df_4.index = df_4.index.map(int)`
  - ex) `col_years = list(map(str, range(2010, 2018)))`
    - map함수는 결과값을 map타입으로 출력하므로 list변환 필요

