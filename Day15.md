# 15์ผ์ฐจ ๐



## ๋ฐ์ดํฐํ๋ ์์ ๊ตฌ์กฐ
- auto-mpg.csv ๋ฐ์ดํฐ์ ์ฌ์ฉ
- mpg(์ฐ๋น), cylindes(์ค๋ฆฐ๋ ์), displacement(๋ฐฐ๊ธฐ๋), horsepower(์ถ๋ ฅ), weight(์ฐจ์ข), acceleration(๊ฐ์๋ฅ๋ ฅ), model_year(์ถ์๋๋), origin(์ ์กฐ๊ตญ), model_name(๋ชจ๋ธ๋ช)์์ผ๋ก ๋์ด



### 1. ๋ฐ์ดํฐํ๋ ์์ ๋ด์ฉ ํ์ธ

- ์๋ถ๋ถ ๋ฏธ๋ฆฌ๋ณด๊ธฐ: `DataFrame๊ฐ์ฒด.head(n)`
- ๋ท๋ถ๋ถ ๋ฏธ๋ฆฌ๋ณด๊ธฐ: `DataFrame๊ฐ์ฒด.tail(n)`

```python
import pandas as pd

# read_csv() ํจ์๋ก df ์์ฑ
df = pd.read_csv('./auto-mpg.csv', header = None)

# ์ด ์ด๋ฆ ์ง์ 
df.columns = ['mpg', 'cylinders', 'displacement', 'horsepower', 'weight',
            'acceleration', 'model_year', 'origin', 'name']

# head, tail ํ์ธ
print(df.head())
print(df.tail())
```

![image](https://user-images.githubusercontent.com/100326309/156331559-7c84dc8d-e6e9-44bf-826f-1982b317471c.png)



### 2. ๋ฐ์ดํฐ์ ์์ฝ ์ ๋ณด ํ์ธํ๊ธฐ

#### 1) ๋ฐ์ดํฐํ๋ ์์ ํฌ๊ธฐ ํ์ธ
- `DataFrame๊ฐ์ฒด.shape`
- ํ๊ณผ ์ด์ ๊ฐ์๋ฅผ ํํ ํํ๋ก ์ถ๋ ฅ (ํ์ ๊ฐ์, ์ด์ ๊ฐ์)

```python
print(df.shape)
```



#### 2) ๋ฐ์ดํฐ์ ๊ธฐ๋ณธ ์ ๋ณด ํ์ธํ๊ธฐ
- `DataFrame๊ฐ์ฒด.info()`
- ๋ฐ์ดํฐํ๋ ์์ ๊ดํ ๊ธฐ๋ณธ ์ ๋ณด๋ฅผ ์ถ๋ ฅ
- ํด๋์ค ์ ํ, ํ ์ธ๋ฑ์ค ๊ตฌ์ฑ, ์ด ์ด๋ฆ์ ์ข๋ฅ์ ๊ฐ์, ๊ฐ ์ด์ ์๋ฃํ๊ณผ ๊ฐ์, ๋ฉ๋ชจ๋ฆฌ ํ ๋น๋์ ๊ดํ ์ ๋ณด ํฌํจ

```python
print(df.info())
```

![image](https://user-images.githubusercontent.com/100326309/156332073-4cf40bbb-5e6a-4cea-8ea3-0cac3e4710c3.png)

- ํ๋ค์ค ์๋ฃํ
    - int64: ์ ์ํ ๋ฐ์ดํฐ
    - float64: ์ค์ํ ๋ฐ์ดํฐ
    - object: ๋ฌธ์์ด ๋ฐ์ดํฐ
    - datetime64, timedelta64: ์๊ฐ ๋ฐ์ดํฐ
- dtypes ์์ฑ์๋ ๊ฐ ์ด์ ๋ํ ์๋ฃํ์ ๊ฐ์๊ฐ ํฌํจ

```python
# dtypes ์์ฑ ํ์ฉํ์ฌ ๊ฐ ์ด์ ์๋ฃํ ํ์ธ
print(df.dtypes)

# ๋ฐ์ดํฐํ๋ ์์ ํน์  ์ด(mpg)์ ์๋ฃํ ํ์ธ
print(df.mpg.dtypes)
```



#### 3) ๋ฐ์ดํฐํ๋ ์์ ๊ธฐ์  ํต๊ณ ์ ๋ณด ์์ฝ
- `Dataframe๊ฐ์ฒด.describe()`
- ์ฐ์ (์ซ์) ๋ฐ์ดํฐ๋ฅผ ๊ฐ๋ ์ด์ ๋ํ ์ฃผ์ ๊ธฐ์  ํต๊ณ ์ ๋ณด(ํ๊ท , ํ์คํธ์ฐจ, ์ต๋๊ฐ, ์ค๊ฐ๊ฐ ๋ฑ)์ ์์ฝํ์ฌ ์ถ๋ ฅ

```python
# df์ ๊ธฐ์ ํต๊ณ ์ ๋ณด ํ์ธ
print(df.describe())

# include์ต์ ์ฌ์ฉํ์ฌ ๊ณ ์ ๊ฐ ๊ฐ์(unique), ์ต๋น๊ฐ(top), ๋น๋์(freq)๊น์ง ์ถ๊ฐ๋ก ํ์ธ
print(df.describe(include = 'all'))
```

![image](https://user-images.githubusercontent.com/100326309/156332135-88982df5-c8a2-435b-97ab-d17862ebd6be.png)



### 3. ํต๊ณ ํจ์ ์ ์ฉ

#### 1) ํ๊ท ๊ฐ

- `DataFrame๊ฐ์ฒด. mean()`
- ์ฐ์  ๋ฐ์ดํฐ๋ฅผ ๊ฐ๋ ๋ชจ๋  ์ด์ ํ๊ท ๊ฐ์ ๊ณ์ฐํ์ฌ ์๋ฆฌ์ฆ ๊ฐ์ฒด๋ก ๋ณํ
- ํน์  ์ด์ ํ๊ท ๊ฐ ํ์ธ: DataFrame๊ฐ์ฒด['์ด ์ด๋ฆ'].mean()

```python
# ์ ์ฒด ์ด์ ํ๊ท ๊ฐ ๊ณ์ฐ
print(df.mean())

# ํน์  ์ด์ ํ๊ท ๊ฐ ๊ณ์ฐ
print(df['mpg'].mean())

# ํน์  ์ด ๋๊ฐ ํ๊ท ๊ฐ
print(df[['mpg', 'weight']].mean())
```



#### 2) ์ค๊ฐ๊ฐ

- `DataFrame๊ฐ์ฒด.median()`
- ์ฐ์  ๋ฐ์ดํฐ๋ฅผ ๊ฐ๋ ๋ชจ๋  ์ด์ ์ค๊ฐ๊ฐ ๊ณ์ฐํ์ฌ ์๋ฆฌ์ฆ๋ก ๋ฐํ

```python
# ์ ์ฒด ์ด์ ์ค๊ฐ๊ฐ
print(df.median())

#ํน์  ์ด์ ์ค๊ฐ๊ฐ
print(df['mpg'].median())
```



#### 3) ์ต๋๊ฐ

- `DataFrame๊ฐ์ฒด.max()`

```python
# ์ ์ฒด ์ด์ ์ต๋๊ฐ
print(df.max())

# ํน์  ์ด์ ์ต๋๊ฐ
print(df['mpg'].max())
```

- ๋ฌธ์์ด์ ASCII ์ซ์๋ก ๋ณํํ์ฌ ํฌ๊ณ  ์์์ ๋น๊ต
- 'horsepower'์ด์๋ "?"๋ฌธ์๊ฐ ํฌํจ๋์ด ์๊ธฐ ๋๋ฌธ์ ์ต๋๊ฐ๋ "?" ์ถ๋ ฅ



#### 4) ์ต์๊ฐ

- `DataFrame๊ฐ์ฒด.min()`

```python
# ์ ์ฒด ์ด์ ์ต์๊ฐ
print(df.min())

# ํน์  ์ด์ ์ต์๊ฐ
print(df['mpg'].min())
```



#### 5) ํ์คํธ์ฐจ

- `DataFrame.std()`
- ํธ์ฐจ: ๊ธฐ๋ณธ ๋ฐ์ดํฐ๊ฐ ํ๊ท ์ผ๋ก๋ถํฐ ์ผ๋ง๋ ๋จ์ด์ ธ ์๋์ง๋ฅผ ์ ์ ์๋ ์ฒ๋

```python
# ์ ์ฒด ์ด์ ํ์คํธ์ฐจ
print(df.std())

# ํน์  ์ด์ ํ์คํธ์ฐจ
print(df['mpg'].std())
```

####  

#### 6) ์๊ด๊ณ์

- `DataFrame.corr()`
- ์ฐ์  ๋ฐ์ดํฐ๋ฅผ ๊ฐ๋ ๋ชจ๋  ์ด์ ๋ํด 2๊ฐ์ฉ ์๋ก ์ง์ ์ง๊ณ , ๊ฐ๊ฐ์ ๊ฒฝ์ฐ์ ๋ํ ์๊ด๊ณ์๋ฅผ ๊ณ์ฐ
- ํน์  ์ด์ ์๊ด๊ณ์: DataFrame๊ฐ์ฒด[์ด ์ด๋ฆ ๋ฆฌ์คํธ].corr()

```python
# ์ ์ฒด ์ด์ ์๊ด๊ณ์
print(df.corr())

# ํน์  ์ด์ ์๊ด๊ณ์
print(df[['mpg', 'weight']].corr())
```

![image](https://user-images.githubusercontent.com/100326309/156332171-a5e84bbb-44f7-4392-842a-6d8e0f50064f.png)

- ์๊ด๊ณ์ ์ ๋๊ฐ์ ํฌ๊ธฐ๋ ์ง์ ๊ด๊ณ์ ๊ฐ๊น์ด ์ ๋๋ฅผ ํํ, ๋ถํธ๋ ์ง์ ๊ด๊ณ์ ๋ฐฉํฅ์ ๋ํ๋
  - r > 0 : ์์ ์๊ด๊ด๊ณ, ์ฐ์ ๋์์ ์ ๋ค์ด ์ฐ์ํฅ๋ฐฉํฅ์ผ๋ก ๋ ๋ฅผ ํ์ฑ(๊ธฐ์ธ๊ธฐ ์์)
  - r < 0 : ์์ ์๊ด๊ด๊ณ, ์ฐ์ ๋์์ ์ ๋ค์ด ์ฐํํฅ๋ฐฉํฅ์ผ๋ก ๋ ๋ฅผ ํ์ฑ(๊ธฐ์ธ๊ธฐ ์์)
  - r = +1 : ๋ชจ๋  ์ ์ด ์ ํํ ๊ธฐ์ธ๊ธฐ๊ฐ ์์์ธ ์ง์  ์์ ์์น
  - r = -1 : ๋ชจ๋  ์ ์ด ์ ํํ ๊ธฐ์ธ๊ธฐ๊ฐ ์์์ธ ์ง์  ์์ ์์น





## ํ๋ค์ค ๋ด์ฅ ๊ทธ๋ํ ๋๊ตฌ ํ์ฉ

### 1. ์  ๊ทธ๋ํ

- `DataFrame๊ฐ์ฒด.plot()`
- ๋จ๋ถํ๋ฐ์ ์ ๋ ฅ๋.xlsx ๋ฐ์ดํฐ ํ์ฉ
  - ์๊ฐ์ ํ๋ฆ์ ๋ฐ๋ฅธ ์ฐ๋๋ณ ๋ฐ์ ๋ ๋ณํ ์ถ์ด๋ฅผ ๋ณด๊ธฐ ์ํด ์ฐ๋ ๊ฐ์ x์ถ์ ํ์ํ๋ ๊ฒ์ด ์ ์ 
  - ์ฐ๋ ๊ฐ์ด ํ ์ธ๋ฑ์ค์ ์์นํ๋๋ก ํ๋ ฌ์ ์ ์นํ์ฌ ๋ฐ์ดํฐํ๋ ์ ์ ์

```python
import pandas as pd

df = pd.read_excel('./๋จ๋ถํ๋ฐ์ ์ ๋ ฅ๋.xlsx')

# ๋จ๋ถํ ๋ฐ์ ๋ ํฉ๊ณ ๋ฐ์ดํฐ ์ถ์ถ
df_ns = df.iloc[[0,5], 2:]

# ํ ์ธ๋ฑ์ค ๋ณ๊ฒฝ
df_ns.index = ['South', 'North']

# ์ด ์ด๋ฆ์ ์๋ฃํ์ ์ ์ํ์ผ๋ก ๋ณ๊ฒฝ
df_ns.columns = df_ns.columns.map(int)

# ์ถ์ถ ๋ฐ์ดํฐ ํ์ธ
print(df_ns)

# ํ๋ ฌ ์ ์น
tdf_ns = df_ns.T

# head ๋ฐ์ดํฐ ํ์ธ
print(tdf_ns.head())

# ์  ๊ทธ๋ํ ๊ทธ๋ฆฌ๊ธฐ
print(tdf_ns.plot())
```

![image](https://user-images.githubusercontent.com/100326309/156332210-66d3bbc7-bd87-45ea-a392-48c1038feb11.png)



### 2. ๋ง๋ ๊ทธ๋ํ

- `DataFrame๊ฐ์ฒด.plot(kind = 'bar')`

```python
print(tdf_ns.plot(kind = 'bar'))
```

![image](https://user-images.githubusercontent.com/100326309/156332232-f56c0494-8561-4634-890c-249ea2f6ef15.png)



### 3. ํ์คํ ๊ทธ๋จ

- `DataFrame๊ฐ์ฒด.plot(kind = 'hist')`
- ๋น๋์ ๊ด๋ จ

```python
print(tdf_ns.plot(kind = 'hist'))
```

![image](https://user-images.githubusercontent.com/100326309/156332271-d0b56e27-82b3-4614-9ac2-ad4cbdd047b3.png)



### 4. ์ฐ์ ๋

- `df.plot(x, y, kind = 'scatter')`
- ''์๋์ฐจ ์ฐ๋น ๋ฐ์ดํฐ์'' ์ด์ฉํ์ฌ ๋ ๋ณ์์ ๊ด๊ณ๋ฅผ ๋ํ๋ด๋ ์ฐ์ ๋ ์ ์
- ์ฝ๋ ํญ๋ชฉ

 	1. plot()ํจ์์ kind = 'scatter' ์ต์ ์ถ๊ฐ
 	2. ๋ฐ์ดํฐํ๋ ์ ์ด ์ค์์ ์๋ก ๋น๊ตํ  ๋ ๋ณ์ ์ ํ
 	 - x์ถ์ ์ฐจ๋ ๋ฌด๊ฒ 'weight'์ด์ ์ง์ 
 	 - y์ถ์ ์ฐ๋น 'mpg'์ด์ ์ง์ 

```python
import pandas as pd

# read_csv() ํจ์๋ก df ์์ฑ
df = pd.read_csv('./auto-mpg.csv', header = None)

# ์ด ์ด๋ฆ ์ง์ 
df.columns = ['mpg', 'cylinders', 'displacement', 'horsepower', 'weight',
            'acceleration', 'model_year', 'origin', 'name']

# ๋ ๊ฐ์ ์ด์ ์ ํํ์ฌ ์ฐ์ ๋ ๊ทธ๋ฆฌ๊ธฐ
print(df.plot(x = 'weight', y = 'mpg', kind = 'scatter'))
```

![image](https://user-images.githubusercontent.com/100326309/156332293-561c2700-5df7-4aec-91a8-b6d91a688dac.png)





### 5. ๋ฐ์ค ํ๋กฏ

- `DataFrame๊ฐ์ฒด.plot(kind = 'box')`
- ํน์  ๋ณ์์ ๋ฐ์ดํฐ ๋ถํฌ์ ๋ถ์ฐ ์ ๋์ ๋ํ ์ ๋ณด๋ฅผ ์ ๊ณต
  - ๋ณ์๋ค์ ๋ฐ์ดํฐ๊ฐ ํผ์ ธ ์๋ ์ ๋๋ฅผ ํ์ธํ  ๋ ์ฌ์ฉ

```python
# ์ด์ ์ ํํ์ฌ ๋ฐ์ค ํ๋กฏ ๊ทธ๋ฆฌ๊ธฐ
print(df[['mpg', 'cylinders']].plot(kind = 'box'))
```

![image](https://user-images.githubusercontent.com/100326309/156332314-85d3064f-c49e-48c0-8a5f-91b4990b4613.png)

- ๊ทธ๋ํ ํด์
  - ๋งจ ์์ ์: ์์น์์ ๋ฒ์ด๋ ๊ฐ
  - ๋ฐ์ค ํ๋กฏ ์ต์๋จ: ์ต๋๊ฐ max
  - ๋ฐ์ค ์๋ถ๋ถ: ๋ถ์์ 75%
  - ๋ฐ์ค ๊ฐ์ด๋ฐ ๋ถ๋ถ: ์ค๊ฐ๊ฐ 50%
  - ๋ฐ์ค ์๋ซ ๋ถ๋ถ: ๋ถ์์ 25%
  - ๋ฐ์ค ํ๋กฏ ์ตํ๋จ: ์ต์๊ฐ min 

- 'cylinders'์ ๋ฐ์ค ํ๋กฏ
  - ์ต๋๊ฐ = ๋ถ์์ 75%
  - ์ค๊ฐ๊ฐ = ๋ถ์์ 25%



## Matplotlib

- 2D ํ๋ฉด ๊ทธ๋ํ์ ๊ดํ ๋ค์ํ ํฌ๋งท๊ณผ ๊ธฐ๋ฅ ์ง์

- ๊ทธ๋ํ ์์๋ฅผ ์ธ์ธํ๊ฒ ๊พธ๋ฏธ๊ธฐ ๊ฐ๋ฅ

- ์ ๋ชฉ ์ง์ 

  - ์ฐจํธ ์ ๋ชฉ ์ถ๊ฐ: `plt.title('์ฐจํธ ์ ๋ชฉ')`

  - ์ถ ์ ๋ชฉ ์ถ๊ฐ: `plt.xlabel('x์ถ ์ ๋ชฉ')`, `plt.ylabel('y์ถ ์ ๋ชฉ')`
  - ์ต์: `size = 10` -> ํฐํธ ํฌ๊ธฐ๋ฅผ 10์ผ๋ก ์ค์ 

- ๋ฒ๋ก ์ถ๊ฐ

  - `plt.legend(labels=['์ด๋ฆ'])`
  - ์ต์: loc, fontsize

- ํ๊ธ ํฐํธ ๋ฌธ์  ํด๊ฒฐ

  - ํ์ด์ฌ ํ๋ก๊ทธ๋จ์ ์๋ถ๋ถ์ ํ๊ธ ํฐํธ๋ฅผ ์ง์ ํ๋ ์ฝ๋ ์ถ๊ฐ

- x์ถ ๋๊ธ ๋ผ๋ฒจ์ ๊ธ์จ๊ฐ ์๋ก ๊ฒน์ณ ์ ๋ณด์ด์ง ์๋ ๋ฌธ์ ๋ฅผ ํด๊ฒฐ

  - ๋๊ธ ๋ผ๋ฒจ์ด ๋ค์ด๊ฐ ๋งํ ์ถฉ๋ถํ ์ฌ์  ๊ณต๊ฐ์ด ์๊ธฐ ๋๋ฌธ์ ๋ฐ์ํ๋ ๋ฌธ์ 
  - ํด๊ฒฐ ๋ฐฉ๋ฒ 2๊ฐ์ง
    - ๊ณต๊ฐ์ ๋ง๋ค๊ธฐ ์ํด `figure()`ํจ์ ์ฌ์ฉํ์ฌ ๊ฐ๋ก ์ฌ์ด์ฆ๋ฅผ ๋ ํฌ๊ฒ ์ค์ 
    - `xticks()` ํจ์ ์ฌ์ฉํ์ฌ x์ถ ๋๊ธ ๋ผ๋ฒจ์ ๋ฐ์๊ณ ๋ฐฉํฅ์ผ๋ก 90๋ ํ์ 

- ์คํ์ผ ์์ ์ง์ 

  - ์, ์คํ์ผ ๋ฑ ๋์์ธ์  ์์๋ฅผ ์ฌ์ ์ ์ง์ ๋ ์คํ์ผ๋ก ๋น ๋ฅด๊ฒ ๋ณ๊ฒฝ ๊ฐ๋ฅ

  - matplotlib ์คํ ํ๊ฒฝ ์ค์ ์ ๋ณ๊ฒฝํ๋ ๊ฒ์ด๋ฏ๋ก ๋ค๋ฅธ ์ฝ๋๋ฅผ ์คํํ  ๋๋ ๊ณ์ ์ ์ฉ๋จ

  - ์์ ์์๋ 'ggplot'์ด๋ผ๋ ์คํ์ผ ์์ ์ง์ : `plt.style.use('ggplot')`

  - plot() ํจ์์ `marker = 'o' `์ต์์ ์ถ๊ฐํ์ฌ ์ ๋ชจ์์ ์ ์ ๋ง์ปค๋ก ํ์
  - ์ข๋ฅ: default, classic, bmh, dark_background, fast, grayscale, seaborn ๋ฑ



### 1. ์  ๊ทธ๋ํ

- ์ฐ์ํ๋ ๋ฐ์ดํฐ ๊ฐ๋ค์ ์ง์  ๋๋ ๊ณก์ ์ผ๋ก ์ฐ๊ฒฐํ์ฌ ๋ฐ์ดํฐ ๊ฐ ์ฌ์ด์ ๊ด๊ณ๋ฅผ ํํ
- ์๊ณ์ด ๋ฐ์ดํฐ์ ๊ฐ์ด ์ฐ์์ ์ธ ๊ฐ์ ๋ณํ์ ํจํด์ ํ์ํ๋ ๋ฐ ์ ํฉ
- `plt.plot(x, y)`

```python
import pandas as pd

# ๋ฐ์ดํฐ ์๊ฐํ์ ์ฌ์ฉํ  matplotlib.pyplot ๋ชจ๋์ import
import matplotlib.pyplot as plt

# matplotlib ํ๊ธ ํฐํธ ์ค๋ฅ ๋ฌธ์  ํด๊ฒฐ
from matplotlib import font_manager, rc
## font_manager๋ ๊ฒฝ๋ก์ ์ด๋ฆ์ ๊ฐ์ง๊ณ  ํฐํธ๋ฅผ ์ง์ 
font_path = "./malgun.ttf"
font_name = font_manager.FontProperties(fname=font_path).get_name()
## rc๋ ํฐํธ๋ฅผ ์ ์ฉ
rc('font', family=font_name)

# Excel ๋ฐ์ดํฐ๋ฅผ ๋ฐ์ดํฐํ๋ ์ ๋ณํ (์ฒซ ์ด์ ํค๋๋ก ์ฌ์ฉ)
df = pd.read_excel("./์๋๋ณ ์ ์ถ์ ์ธ๊ตฌ์.xlsx", header = 0)

# ๋๋ฝ๊ฐ(NaN)์ ์ ๋ฐ์ดํฐ๋ก ์ฑ์(์์ ์์ ๋ณํฉ)
df = df.fillna(method='ffill')

# ์์ธ์์ ๋ค๋ฅธ ์ง์ญ์ผ๋ก ์ด๋ํ ๋ฐ์ดํฐ๋ง ์ถ์ถ
mask = (df['์ ์ถ์ง๋ณ'] == '์์ธํน๋ณ์') & (df['์ ์์ง๋ณ'] != '์์ธํน๋ณ์')
df_seoul = df[mask]

# '์ ์ถ์ง๋ณ' ์ด์ ํ์ ์์ผ๋ฏ๋ก ์ญ์ 
df_seoul = df_seoul.drop(['์ ์ถ์ง๋ณ'], axis=1)

# '์ ์์ง๋ณ' ์ด์ '์ ์์ง'๋ก ์ด๋ฆ ๋ณ๊ฒฝ ํ ํ์ธ๋ฑ์ค๋ก ์ค์ 
df_seoul.rename({'์ ์์ง๋ณ': '์ ์์ง'}, axis=1, inplace=True)
df_seoul.set_index('์ ์์ง', inplace=True)

# ์์ธ์์ ๊ฒฝ๊ธฐ๋๋ก ์ด๋ํ ์ธ๊ตฌ ๋ฐ์ดํฐ ๊ฐ๋ง ์ ํ
dt_g = df_seoul.loc['๊ฒฝ๊ธฐ๋']

# ์คํ์ผ ์์ ์ง์ 
plt.style.use('ggplot')

# ๊ทธ๋ฆผ ์ฌ์ด์ฆ ์ง์ (๊ฐ๋ก 14์ธ์น, ์ธ๋ก 5์ธ์น)
plt.figure(figsize = (14,5))

# x์ถ ๋๊ธ ๋ผ๋ฒจ ํ์ 
plt.xticks(rotation = 'vertical')

# 1) x, y์ถ ๋ฐ์ดํฐ๋ฅผ plot()ํจ์์ ์ง์  ์๋ ฅ (๋ง์ปค ํ์ ์ถ๊ฐ)
plt.plot(dt_g.index, dt_g.values, marker = 'o', markersize = 10) 

# 2) ํ๋ค์ค ๊ฐ์ฒด๋ฅผ plot()ํจ์์ ์๋ ฅ
# plt.plot(dt_g)

# ์ฐจํธ ์ ๋ชฉ ์ถ๊ฐ
plt.title('์์ธ -> ๊ฒฝ๊ธฐ ์ธ๊ตฌ ์ด๋', size = 30)

# ์ถ ์ด๋ฆ ์ถ๊ฐ
plt.xlabel('๊ธฐ๊ฐ', size = 20)
plt.ylabel('์ธ๊ตฌ ์ด๋ ์', size = 20)

# ๋ฒ๋ก ์ถ๊ฐ
plt.legend(labels=['์์ธ -> ๊ฒฝ๊ธฐ'], loc='best', fontsize=15)

# ์ฐจํธ ์๊ฐํ
plt.show
```

- 17ํ ์ถ๊ฐ ์ค๋ช) 

  - '์ ์ถ์ง๋ณ' ์ด์๋ ๋๋ฝ ๋ฐ์ดํฐ(NaN) ๋ค์ ์กด์ฌ
  - Excel ํ์ผ์์ ๋ณํฉ๋ ์์ ๋ฐ์ดํฐํ๋ ์์ผ๋ก ๋ณํํ  ๋ ์ ์ ํ ๊ฐ์ ์ฐพ์ง ๋ชปํด ๋ฐ์

  - method = 'ffill'์ต์์ ์ฌ์ฉํ์ฌ ๋๋ฝ ๋ฐ์ดํฐ๊ฐ ์๋ ํ์ ๋ฐ๋ก ์์ ์์นํ ๋ฐ์ดํฐ ๊ฐ์ผ๋ก ์ฑ์

- 38ํ ์ถ๊ฐ ์ค๋ช)

  - ๊ธ์จ๋ฅผ ํ์ ํ๊ธฐ ์ํด ์ฌ์ฉํ rotation = 'vertical' ๋์  ๊ฐ๋๋ฅผ ๋ํ๋ด๋ ์ซ์๋ก ํํํ  ์ ์์. 
  - ex) rotation = 90 -> ๋ฐ์๊ณ ๋ฐฉํฅ์ผ๋ก 90๋ ํ์  

![image](https://user-images.githubusercontent.com/100326309/156332348-4ef46ad0-b6a9-49be-bf8b-3c3416f53039.png)