# 16μΌμ°¨ π



## Matplotlib κ·Έλν μ¬ν



### 1. μ€λͺμ λ§λΆμ΄λ μ£Όμ

- `annotate()` ν¨μ: νμ΄νμ νμ€νΈ μμΉλ₯Ό μ‘μμ λ°°μΉ
    - μμΉλ₯Ό λνλ΄λ (x,y) μ’νμμ xκ°μ μΈλ±μ€ λ²νΈ μ¬μ©
    - yκ°: μ€μ  yκ° (μμ : μΈκ΅¬μ λ°μ΄ν° μ«μκ°)
    - `rotation μ΅μ`: μμ νμ  λ°©ν₯μ λ°μκ³ λ°©ν₯
    - `va/ha `μ΅μ: νμ€νΈ μ λ ¬ (μν/μ’μ°)
- `arrowprops μ΅μ`: νμ΄ν μ£Όμ 
    - νμ΄ν μ€νμΌ, μμμ κ³Ό λμ μ μ’νλ₯Ό μλ ₯
- μμ μμλ μ£Όμμ λ£μ μ¬λ°± κ³΅κ°μ νλ³΄νκΈ° μν΄ `ylim()` ν¨μλ₯Ό μ¬μ©νμ¬ yμΆμ λ²μ μ¦κ°

```python
# yμΆ λ²μ μ§μ  (μ΅μκ°, μ΅λκ°)
plt.ylim(50000, 800000)

# μ£Όμ νμ - νμ΄ν
plt.annotate('', 
             xy=(20, 620000),    # νμ΄νμ λ¨Έλ¦¬ λΆλΆ(λμ )
             xytext=(2, 290000), # νμ΄νμ κΌ¬λ¦¬ λΆλΆ(μμμ )
             xycoords='data',    # μ’νμ²΄κ³ 
             # νμ΄ν μμ
             # dict : νμ΄νμ νΉμ±μ μ§μ 
             # lw : νμ΄νμ λκ»
             arrowprops=dict(arrowstyle='->', color='skyblue', lw=5)
            )

plt.annotate('', 
             xy=(44, 450000),    # νμ΄νμ λ¨Έλ¦¬ λΆλΆ(λμ )
             xytext=(30, 600000), # νμ΄νμ κΌ¬λ¦¬ λΆλΆ(μμμ )
             xycoords='data',    # μ’νμ²΄κ³ 
             # νμ΄ν μμ
             # dict : νμ΄νμ νΉμ±μ μ§μ 
             # lw : νμ΄νμ λκ»
             arrowprops=dict(arrowstyle='->', color='skyblue', lw=5)
            )

# μ£Όμ νμ - νμ€νΈ
plt.annotate('μΈκ΅¬μ΄λ μ¦κ°(1970-1995)',  # νμ€νΈ μλ ₯ 
             xy=(10, 500000),             # νμ€νΈ μμΉ κΈ°μ€μ (μ€κ°)
             rotation=24,                 # νμ€νΈ νμ  κ°λ
             va='center',                 # νμ€νΈ μν μ λ ¬('center', 'top', 'bottom')
             ha='center',                 # νμ€νΈ μ’μ° μ λ ¬('center', 'left', 'right'),
             fontsize=15
            )

plt.annotate('μΈκ΅¬μ΄λ κ°μ(1995-2017)',  # νμ€νΈ μλ ₯ 
             xy=(37, 580000),             # νμ€νΈ μμΉ κΈ°μ€μ (μ€κ°)
             rotation=-13,                 # νμ€νΈ νμ  κ°λ
             va='center',                 # νμ€νΈ μν μ λ ¬('center', 'top', 'bottom')
             ha='center',                 # νμ€νΈ μ’μ° μ λ ¬('center', 'left', 'right'),
             fontsize=15
            )
```

![image](https://user-images.githubusercontent.com/100326309/156531192-c082af00-946a-44e7-a69c-79ac1907e647.png)



### 2. axe κ°μ²΄

#### 1) νλ©΄μ λΆν νμ¬ κ·Έλν μ¬λ¬ κ° κ·Έλ¦¬κΈ° 

μ¬λ¬ κ°μ axe κ°μ²΄λ₯Ό μμ±, λΆν λ νλ©΄λ§λ€ axe κ°μ²΄λ₯Ό νλμ© λ°°μ 

- axe κ°μ²΄λ κ°κ° μλ‘ λ€λ₯Έ κ·Έλν νν κ°λ₯
- ν νλ©΄μμ μ¬λ¬ κ°μ κ·Έλνλ₯Ό λΉκ΅νκ±°λ λ€μν μ λ³΄λ₯Ό λμμ λ³΄μ¬μ€ λ μ¬μ©

- `figure()`: κ·Έλνλ₯Ό κ·Έλ¦¬λ κ·Έλ¦Όν μμ±

  - `figsize μ΅μ`: (κ°λ‘, μΈλ‘) κ·Έλ¦Όν ν¬κΈ° μ§μ 

- `add_subplot(νμ κ°μ, μ΄μ κ°μ, μλΈνλ‘― μμ)` : κ·Έλ¦Όνμ μ¬λ¬ κ°λ‘ λΆν 

  - ex) `ax1 = fig.add_subplot(2, 1, 1)`

- `plot(x,y)`: axe κ°μ²΄μ κ·Έλν κ·Έλ¦¬κΈ°

  - marker : λ§μ»€μ λͺ¨μ('o', '+', '*', '.')

  - markerfacecolor : λ§μ»€μ λ°°κ²½μ

  - markersize : λ§μ»€μ ν¬κΈ°

  - color: μ μ μ

  - linewidth: μ μ λκ»

  - label: λ²λ‘ μ§μ 

- μμ μμλ μ μΌλ‘λ§ κ΅¬μ±λ κ·Έλνμ μ , μ μΌλ‘ κ΅¬μ±λ κ·Έλν λ κ° μμ±

```python
# κ·Έλν κ°μ²΄ μμ±
fig  = plt.figure(figsize = (10,10))
ax1 = fig.add_subplot(2,1,1)
ax2 = fig.add_subplot(2,1,2)

# axe κ°μ²΄μ plot ν¨μλ‘ κ·Έλν μΆλ ₯
ax1.plot(dt_g, 'o', markersize = 10)
ax2.plot(dt_g, marker = 'o', markerfacecolor = 'green', markersize = 10,
        color = 'olive', linewidth = 2, label = 'μμΈ->κ²½κΈ°')
ax2.legend(loc = 'best') # λ²λ‘ μμΉ

plot.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531261-b36c814f-9984-41a2-8696-da452f37ad8d.png)



#### 2) axe κ°μ²΄ κ·Έλνμ μ λͺ©, μΆ μ΄λ¦ μΆκ°

- `set_title()` : μ λͺ© μΆκ°
- `set_xlabel()`: xμΆ μ΄λ¦ μ§μ 
- `set_ylable()`: yμΆ μ΄λ¦ μ§μ 
- `set_xticklabels`: μΆ λκΈ λΌλ²¨ νμ 
- `tick_params()`: μΆ λκΈ λΌλ²¨μ ν¬κΈ°

```python
# μ°¨νΈ μ λͺ© μΆκ°
ax.set_title('μμΈ -> κ²½κΈ° μΈκ΅¬ μ΄λ', size = 20)

# μΆ μ΄λ¦ μΆκ°
ax.set_xlabel('κΈ°κ°', size = 12)
ax.set_ylabel('μ΄λ μΈκ΅¬ μ', size = 12)

# μΆ λκΈ λΌλ²¨ νμ 
ax.set_xticklabels(dt_g.index, rotation = 90)

# μΆ λκΈ λΌλ²¨ ν¬κΈ°
ax.tick_params(axis = "x", labelsize = 10)
ax.tick_params(axis = "y", labelsize = 10)
```

![image](https://user-images.githubusercontent.com/100326309/156531289-3a146fdd-dc79-4fd3-9e0e-a7e6ccc9bb46.png)



#### 3) ν νλ©΄μ μ¬λ¬ κ°μ κ·Έλν κ·Έλ¦¬κΈ°

- μμΈνΉλ³μμμ μΆ©μ²­λΆλ, μ λΌλ¨λ, κ²½μλΆλλ‘ μ΄λν μΈκ΅¬ λ³ν κ·Έλν 3κ°λ₯Ό νλμ νλ©΄μ μΆλ ₯
- κ·Έλν κ°μ²΄ 1κ° μμ±: `add_subplot(1, 1, 1)`
- κ° μ§μ­μ ν΄λΉνλ ν λ°μ΄ν° μ ν, μ  κ·Έλνλ₯Ό μΆλ ₯νλ `plot()`λ©μλλ₯Ό 3λ² μ μ©

```python
import pandas as pd

# λ°μ΄ν° μκ°νμ μ¬μ©ν  matplotlib.pyplot λͺ¨λμ import
import matplotlib.pyplot as plt

# matplotlib νκΈ ν°νΈ μ€λ₯ λ¬Έμ  ν΄κ²°
from matplotlib import font_manager, rc
## font_managerλ κ²½λ‘μ μ΄λ¦μ κ°μ§κ³  ν°νΈλ₯Ό μ§μ 
font_path = "./malgun.ttf"
font_name = font_manager.FontProperties(fname=font_path).get_name()
## rcλ ν°νΈλ₯Ό μ μ©
rc('font', family=font_name)

# Excel λ°μ΄ν°λ₯Ό λ°μ΄ν°νλ μ λ³ν (μ²« μ΄μ ν€λλ‘ μ¬μ©)
df = pd.read_excel("./μλλ³ μ μΆμ μΈκ΅¬μ.xlsx", header = 0)

# λλ½κ°(NaN)μ μ λ°μ΄ν°λ‘ μ±μ(μμ μμ λ³ν©)
df = df.fillna(method='ffill')

# μμΈμμ λ€λ₯Έ μ§μ­μΌλ‘ μ΄λν λ°μ΄ν°λ§ μΆμΆ
mask = (df['μ μΆμ§λ³'] == 'μμΈνΉλ³μ') & (df['μ μμ§λ³'] != 'μμΈνΉλ³μ')
df_seoul = df[mask]

# 'μ μΆμ§λ³' μ΄μ νμ μμΌλ―λ‘ μ­μ 
df_seoul = df_seoul.drop(['μ μΆμ§λ³'], axis=1)

# 'μ μμ§λ³' μ΄μ 'μ μμ§'λ‘ μ΄λ¦ λ³κ²½ ν νμΈλ±μ€λ‘ μ€μ 
df_seoul.rename({'μ μμ§λ³': 'μ μμ§'}, axis=1, inplace=True)
df_seoul.set_index('μ μμ§', inplace=True)

# μμΈμμ 'μΆ©μ²­λΆλ', 'μ λΌλ¨λ', 'κ²½μλΆλ'λ‘ μ΄λν μΈκ΅¬ λ°μ΄ν° κ°λ§ μ ν
col_years = list(map(str, range(1970, 2018)))
df_3 = df_seoul.loc[['μΆ©μ²­λΆλ', 'μ λΌλ¨λ', 'κ²½μλΆλ'], col_years]

# μ€νμΌ μμ μ§μ 
plt.style.use('ggplot')

# κ·Έλν κ°μ²΄ μμ±
fig = plt.figure(figsize=(20, 5))
ax = fig.add_subplot(1, 1, 1)

# axe κ°μ²΄μ plot() ν¨μλ‘ κ·Έλν μΆλ ₯
ax.plot(col_years, df_3.loc['μΆ©μ²­λΆλ', :], marker='o', markerfacecolor='green',
        markersize=10, color='olive', linewidth=2, label='μμΈ -> μΆ©λΆ')
ax.plot(col_years, df_3.loc['μ λΌλ¨λ', :], marker='o', markerfacecolor='blue',
        markersize=10, color='skyblue', linewidth=2, label='μμΈ -> μ λ¨')
ax.plot(col_years, df_3.loc['κ²½μλΆλ', :], marker='o', markerfacecolor='red',
        markersize=10, color='magenta', linewidth=2, label='μμΈ -> κ²½λΆ')

ax.legend(loc='best')

# μ°¨νΈ μ λͺ© μΆκ°
ax.set_title('μμΈ -> μΆ©λΆ, μ λ¨, κ²½λΆ μΈκ΅¬ μ΄λ', size=20)

# μΆ μ΄λ¦ μΆκ°
ax.set_xlabel('κΈ°κ°', size=12)
ax.set_ylabel('μ΄λ μΈκ΅¬μ', size=12)

# μΆ λκΈ λΌλ²¨μ νμ 
ax.set_xticklabels(col_years, rotation=90)

# μΆ λκΈ λΌλ²¨ ν¬κΈ°
ax.tick_params(axis="x", labelsize=10)
ax.tick_params(axis="y", labelsize=10)

plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531319-45b2cb79-206b-431f-969c-61b1e231259a.png)



#### 4) μ¬λ¬ νλ©΄μ μ¬λ¬ κ°μ κ·Έλν κ·Έλ¦¬κΈ°

- axe κ°μ²΄ 4κ° μμ±: `ax1 = fig.add_subplot(2, 2, 1~4)` -> 2ν 2μ΄
- κ·Έλν 4κ° μΆλ ₯: `ax1.plot(col_years, df_4.loc['μΆ©μ²­λΆλ', :]` -> yκ° κ°κ°μ λ§λ λ°μ΄ν° μ ν
- κ·Έλν λμμΈ λͺ¨λ λ°λ‘ μ½λ μμ± (or for λ°λ³΅λ¬Έ)

```python
# μμΈμμ 'μΆ©μ²­λΆλ', 'μ λΌλ¨λ', 'κ²½μλΆλ, κ°μλ'λ‘ μ΄λν μΈκ΅¬ λ°μ΄ν° κ°λ§ μ ν
col_years = list(map(str, range(1970, 2018)))
df_4 = df_seoul.loc[['μΆ©μ²­λΆλ', 'μ λΌλ¨λ', 'κ²½μλΆλ', 'κ°μλ'], col_years]

# μ€νμΌ μμ μ§μ 
plt.style.use('ggplot')

# κ·Έλν κ°μ²΄ μμ±
fig = plt.figure(figsize=(20, 20))
ax1 = fig.add_subplot(2, 2, 1)
ax2 = fig.add_subplot(2, 2, 2)
ax3 = fig.add_subplot(2, 2, 3)
ax4 = fig.add_subplot(2, 2, 4)

# axe κ°μ²΄μ plot() ν¨μλ‘ κ·Έλν μΆλ ₯
ax1.plot(col_years, df_4.loc['μΆ©μ²­λΆλ', :], marker='o', markerfacecolor='green',
        markersize=10, color='olive', linewidth=2, label='μμΈ -> μΆ©λΆ')
ax2.plot(col_years, df_4.loc['μ λΌλ¨λ', :], marker='o', markerfacecolor='blue',
        markersize=10, color='skyblue', linewidth=2, label='μμΈ -> μ λ¨')
ax3.plot(col_years, df_4.loc['κ²½μλΆλ', :], marker='o', markerfacecolor='red',
        markersize=10, color='magenta', linewidth=2, label='μμΈ -> κ²½λΆ')
ax4.plot(col_years, df_4.loc['κ°μλ', :], marker='o', markerfacecolor='red',
        markersize=10, color='yellow', linewidth=2, label='μμΈ -> κ°μ')

ax1.legend(loc='best')
ax2.legend(loc='best')
ax3.legend(loc='best')
ax4.legend(loc='best')

# μ°¨νΈ μ λͺ© μΆκ°
ax1.set_title('μμΈ -> μΆ©λΆ μΈκ΅¬ μ΄λ', size=20)
ax2.set_title('μμΈ -> μ λ¨ μΈκ΅¬ μ΄λ', size=20)
ax3.set_title('μμΈ -> κ²½λΆ μΈκ΅¬ μ΄λ', size=20)
ax4.set_title('μμΈ -> κ°μ μΈκ΅¬ μ΄λ', size=20)

# μΆ μ΄λ¦ μΆκ°
ax1.set_xlabel('κΈ°κ°', size=12)
ax1.set_ylabel('μ΄λ μΈκ΅¬μ', size=12)
ax2.set_xlabel('κΈ°κ°', size=12)
ax2.set_ylabel('μ΄λ μΈκ΅¬μ', size=12)
ax3.set_xlabel('κΈ°κ°', size=12)
ax3.set_ylabel('μ΄λ μΈκ΅¬μ', size=12)
ax4.set_xlabel('κΈ°κ°', size=12)
ax4.set_ylabel('μ΄λ μΈκ΅¬μ', size=12)

# μΆ λκΈ λΌλ²¨μ νμ 
ax1.set_xticklabels(col_years, rotation=90)
ax2.set_xticklabels(col_years, rotation=90)
ax3.set_xticklabels(col_years, rotation=90)
ax4.set_xticklabels(col_years, rotation=90)

# μΆ λκΈ λΌλ²¨ ν¬κΈ°
ax1.tick_params(axis="x", labelsize=10)
ax1.tick_params(axis="y", labelsize=10)
ax2.tick_params(axis="x", labelsize=10)
ax2.tick_params(axis="y", labelsize=10)
ax3.tick_params(axis="x", labelsize=10)
ax3.tick_params(axis="y", labelsize=10)
ax4.tick_params(axis="x", labelsize=10)
ax4.tick_params(axis="y", labelsize=10)

''''
#for λ°λ³΅λ¬Έ
for i in range(0,4):
    ax[i].set_xlabel('κΈ°κ°', size=12)
    ax[i].set_ylabel('μ΄λ μΈκ΅¬μ', size=12)
    ax[i].legend(loc='best')
    ax[i].set_xticklabels(dt_g.index, rotation=90)
    ax[i].tick_params(axis="x", labelsize=10)
    ax[i].tick_params(axis="y", labelsize=10)
''''
fig.tight_layout()

plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531353-d853da8f-cd9d-480d-a4fd-2f56357ece4e.png)



#### 5) κ·Έλν κ°κ²© μ‘°μ 

- μλμ‘°μ : `tight_layout()` 
  - ex) `fig.tight_layout()`

- μ§μ  μ‘°μ : `subplots_adjust()`

  - ex) `plt.subplts_adjust()`

  - left, right, top, bottom, wspace(μλΈ νλ‘― μ¬μ΄μ μ’μ° μλΉ κ³΅κ°), hspace(μλΈ νλ‘― μ¬μ΄μ μν μλΉ κ³΅κ°)



### 3. Matplotlibμμ μ¬μ©ν  μ μλ μμ νμΈνκΈ°

``` python
import matplotlib

# μ»¬λ¬ μ λ³΄λ₯Ό λ°μμ¬ λ³μ
colors = {}

for name, hex in matplotlib.colors.cnames.items():
    colors[name] = hex
    
print(colors)
```

---



## λ©΄μ  κ·Έλν (area plot)

- `plot(kind = 'area')`
- κ° μ΄μ λ°μ΄ν°λ₯Ό μ  κ·Έλνλ‘ κ΅¬ν, μ  κ·Έλνμ xμΆ μ¬μ΄μ κ³΅κ°μ μ μ μ©

- μμ ν¬λͺλ μ§μ : κΈ°λ³Έκ°: 0.5, λ²μ: 0~1
- `stacked μ΅μ`: κ·Έλν λμ  μ¬λΆ μ€μ  (κΈ°λ³Έκ°: `stacked = True`)
  - κ° μ΄μ μ  κ·Έλνλ₯Ό λ€λ₯Έ μ΄μ μ  κ·Έλν μλ‘ μμμ¬λ¦¬λ λ°©μ
  - κ° μ΄μ ν¨ν΄κ³Ό μ΄ μ μ²΄μ ν©κ³κ° μ΄λ»κ² λ³νλμ§ νμΈ

```python
import pandas as pd

# λ°μ΄ν° μκ°νμ μ¬μ©ν  matplotlib.pyplot λͺ¨λμ import
import matplotlib.pyplot as plt

# matplotlib νκΈ ν°νΈ μ€λ₯ λ¬Έμ  ν΄κ²°
from matplotlib import font_manager, rc
## font_managerλ κ²½λ‘μ μ΄λ¦μ κ°μ§κ³  ν°νΈλ₯Ό μ§μ 
font_path = "./malgun.ttf"
font_name = font_manager.FontProperties(fname=font_path).get_name()
## rcλ ν°νΈλ₯Ό μ μ©
rc('font', family=font_name)

# Excel λ°μ΄ν°λ₯Ό λ°μ΄ν°νλ μ λ³ν (μ²« μ΄μ ν€λλ‘ μ¬μ©)
df = pd.read_excel("./μλλ³ μ μΆμ μΈκ΅¬μ.xlsx", header = 0)

# λλ½κ°(NaN)μ μ λ°μ΄ν°λ‘ μ±μ(μμ μμ λ³ν©)
df = df.fillna(method='ffill')

# μμΈμμ λ€λ₯Έ μ§μ­μΌλ‘ μ΄λν λ°μ΄ν°λ§ μΆμΆ
mask = (df['μ μΆμ§λ³'] == 'μμΈνΉλ³μ') & (df['μ μμ§λ³'] != 'μμΈνΉλ³μ')
df_seoul = df[mask]

# 'μ μΆμ§λ³' μ΄μ νμ μμΌλ―λ‘ μ­μ 
df_seoul = df_seoul.drop(['μ μΆμ§λ³'], axis=1)

# 'μ μμ§λ³' μ΄μ 'μ μμ§'λ‘ μ΄λ¦ λ³κ²½ ν νμΈλ±μ€λ‘ μ€μ 
df_seoul.rename({'μ μμ§λ³': 'μ μμ§'}, axis=1, inplace=True)
df_seoul.set_index('μ μμ§', inplace=True)

# μμΈμμ 'μΆ©μ²­λΆλ', 'μ λΌλ¨λ', 'κ²½μλΆλ'λ‘ μ΄λν μΈκ΅¬ λ°μ΄ν° κ°λ§ μ ν
col_years = list(map(str, range(1970, 2018)))
df_4 = df_seoul.loc[['μΆ©μ²­λΆλ', 'μ λΌλ¨λ', 'κ²½μλΆλ', 'κ°μλ'], col_years]
df_4 = df_4.T

# μ€νμΌ μμ μ§μ 
plt.style.use('ggplot')

# λ°μ΄ν°νλ μ μΈλ±μ€λ₯Ό μ μν λ³κ²½
df_4.index = df_4.index.map(int)

# λ©΄μ  κ·Έλν κ·Έλ¦¬κΈ° (λμ x)
df_4.plot(kind = 'area', stacked = False, alpha = 0.2, figsize = (20,10))
# (λμ o) df_4.plot(kind = 'area', stacked = True, alpha = 0.2, figsize = (20,10))

plt.title('μμΈ -> ν μλ μΈκ΅¬ μ΄λ', size = 30)
plt.xlabel('κΈ°κ°', size = 20)
plt.ylabel('μ΄λ μΈκ΅¬ μ', size = 20)
plt.legend(loc = 'best', fontsize = 15)

plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531399-85bddd4a-64e5-4e97-bead-e8002019b8ce.png)



## λ§λ κ·Έλν (bar plot)

- `plot(kind = 'bar')` / `plot(kind = 'barh')`
- λ°μ΄ν° κ°μ ν¬κΈ°μ λΉλ‘νμ¬ λμ΄λ₯Ό κ°λ μ§μ¬κ°ν λ§λλ‘ νν
- λ°μ΄ν° κ°μ μ°¨μ΄λ₯Ό ν¨κ³Όμ μΌλ‘ μ€λͺ

```python
# μΈλ‘ν λ§λ κ·Έλν κ·Έλ¦¬κΈ°
df_4.plot(kind = 'bar', figsize = (20,10), width = 0.7,
         color = ['orange', 'green', 'red', 'blue'])

# κ°λ‘ν λ§λ κ·Έλν κ·Έλ¦¬κΈ°
df_4.plot(kind = 'barh', figsize = (20,10), width = 0.7,
         color = ['orange', 'green', 'red', 'blue'])
```

![image](https://user-images.githubusercontent.com/100326309/156531427-9b044ea8-f76e-4e3b-ac4d-62f02296f3ce.png)

```python
# ν©κ³ κ·Έλν κ·Έλ¦¬κΈ° (κ°λ‘ν)
# 2010-2017λ μ΄λ μΈκ΅¬ μλ₯Ό ν©κ³νμ¬ μλ‘μ΄ μ΄λ‘ μΆκ°
df_4['ν©κ³'] = df_4.sum(axis = 1)

# κ°μ₯ ν° κ°λΆν° μ λ ¬
df_total = df_4[['ν©κ³']].sort_values(by = 'ν©κ³', ascending = True)

# κ·Έλν κ·Έλ¦¬κΈ°
df_total.plot(kind = 'barh', figsize = (10, 3), width = 0.5,
         color = ['skyblue'])
```

![image](https://user-images.githubusercontent.com/100326309/156531468-00e8b964-66c6-48f9-a5f9-3938867cdbca.png)





## νμ€ν κ·Έλ¨ (histogram)

- `plot(kind = 'hist')`

- λ³μκ° νλμΈ λ¨λ³μ λ°μ΄ν°μ λΉλμλ₯Ό κ·Έλνλ‘ νν
- xμΆμ κ°μ ν¬κΈ°μ μ¬λ¬ κ΅¬κ°μΌλ‘ λλκ³ , κ° κ΅¬κ°μ μνλ λ°μ΄ν° κ°μ κ°μ(λΉλ)

```python
import pandas as pd
import matplotlib.pyplot as plt

# μ€νμΌ μμ μ§μ 
plt.style.use('bmh')

# df μμ±
df = pd.read_csv('./auto-mpg.csv', header = None)

# μ΄ μ΄λ¦ μ§μ 
df.columns = ['mpg', 'cylinders', 'displacement', 'horsepower', 'weight',
            'acceleration', 'model_year', 'origin', 'name']

# νμ€ν κ·Έλ¨ κ·Έλν κ·Έλ¦¬κΈ°
df['mpg'].plot(kind = 'hist', bins = 10, color = 'coral', figsize = (10,5))

plt.title('Histogram')
plt.xlabel('mpg')
plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531498-18f9a088-f914-48fe-9131-1a8ab49324c2.png)



## μ°μ λ (scatter)

- `plot(kind = 'scatter', x, y)`
- μλ‘ λ€λ₯Έ λ λ³μ μ¬μ΄μ κ΄κ³λ₯Ό νν
- μ μ μμ(c), ν¬κΈ°(s) μ΅μ

```python
# μ°μ λ κ·Έλν κ·Έλ¦¬κΈ°
df.plot(kind='scatter', x='weight', y='mpg', 
        c='coral', s=10, figsize=(10, 5))
plt.title('Scatter Plot - mpg vs weight')
plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531534-71ab9e6e-799b-48cf-9589-854e57049343.png)

- μ°μ λμμ μλ‘μ΄ λ³μλ₯Ό μΆκ°νμ¬ μ μ ν¬κΈ° λλ μμμΌλ‘ νν κ°λ₯
  - μλ‘μ΄ λ³μλ‘ μ€λ¦°λ κ°μ('cylinders'μ΄) μΆκ°
  - μ€λ¦°λ κ°μλ₯Ό λνλ΄λ μ μλ₯Ό κ·Έλλ‘ μ°λ, ν΄λΉ μ΄μ μ΅λκ° λλΉ μλμ  ν¬κΈ°λ₯Ό λνλ΄λ λΉμ¨μ κ³μ°νμ¬ `'cylinders_size'`λ³μμ μ μ₯
  - μ μ ν¬κΈ°μ λ³νλ₯Ό μ£ΌκΈ° λλ¬Έμ λΉλλ°©μΈκ³Ό λΉμ·νμ¬ **'λ²λΈμ°¨νΈ'**λΌκ³  λΆλ¦

```python
# cylinders_size λ³μ μμ±
cylinders_size = df.cylinders / df.cylinders.max() * 300

# cylinders_sizeμ λ°λΌ μ μ ν¬κΈ°κ° λ€λ₯Έ λ²λΈμ°¨νΈ κ·Έλ¦¬κΈ°
# alpha : ν¬λͺλ
df.plot(kind='scatter', x='weight', y='mpg', c='coral', s=cylinders_size, 
        figsize=(10, 5), alpha=0.3) 
plt.title('Scatter Plot - mpg vs weight')
plt.show()

# cylinders_sizeμ λ°λΌ μ μ μμμ΄ λ€λ₯Έ λ²λΈμ°¨νΈ κ·Έλ¦¬κΈ°
# marker : μ­μ(+)λ‘
# cmap: 'viridis' μ»¬λ¬λ§΅ μ¬μ©
df.plot(kind='scatter', x='weight', y='mpg', marker='+', c=cylinders_size, 
        cmap='viridis', s=50, figsize=(10, 5), alpha=0.3)
plt.title('Scatter Plot - mpg vs weight')
```

![image](https://user-images.githubusercontent.com/100326309/156531558-91df5f68-217b-4165-9716-48fca605a6e1.png)

![image](https://user-images.githubusercontent.com/100326309/156531590-d41fff4a-d1fe-49d9-a06b-a83a294d3869.png)



## νμ΄μ°¨νΈ (pie chart)

- `plot(kind = 'pie')`

- μμ νμ΄ μ‘°κ°μ²λΌ λλμ΄μ νν
  - λ°μ΄ν° κ°μ ν¬κΈ°μ λΉλ‘

- μμ 

  - λ°μ΄ν° κ°μλ₯Ό μΈκΈ° μν΄ μ«μ 1μ μμλ‘ κ°λ 'count' μ΄μ μμ±

  - `groupby()` ν¨μλ₯Ό μ¬μ©νμ¬ 'μ μ‘°κ΅­κ°'λ₯Ό 3κ°μ κ·Έλ£ΉμΌλ‘ λλ

  - `sum()` ν¨μλ₯Ό μ¬μ©νμ¬ κ·Έλ£Ήλ³ κ°μμ ν©κ³λ₯Ό κ³μ°

```python
# λ°μ΄ν° κ°μ μΉ΄μ΄νΈλ₯Ό μν΄ κ° 1μ μμλ‘ κ°λ μ΄μ μΆκ°
df['count'] = 1

# origin μ΄μ κΈ°μ€μΌλ‘ κ·Έλ£Ήν, ν©κ³ μ°μ°
df_origin = df.groupby('origin').sum()
print(df_origin)

# μ μ‘°κ΅­κ° μ΄λ¦ λ³κ²½
df_origin.index = ['USA', 'EU', 'JAPAN']

# count μ΄μ μ¬μ©νμ¬ νμ΄ μ°¨νΈ λ§λ€κΈ°
df_origin['count'].plot(kind='pie', figsize=(7, 5), autopct='%0.1f%%',
                        startangle=10, colors=['chocolate', 'bisque', 'cadetblue'])

plt.title('Model Origin', size=20)
plt.axis('equal')
plt.legend(labels=df_origin.index, loc='upper right')

plt.show()
```

![image](https://user-images.githubusercontent.com/100326309/156531612-a7ddbf21-7379-4501-bae2-c662eaa2c1c4.png)





## λ°μ€νλ‘― (box plot)

- μ μ‘°κ΅­κ°λ³ μ°λΉ λΆν¬λ₯Ό λ³΄μ¬μ£Όλ λ°μ€ νλ‘― κ·Έλ¦¬κΈ°

  - κ·Έλ¦Όνμ 2κ°μ axe κ°μ²΄λ‘ λΆν νκΈ° μν΄μ `add_subplot()` ν¨μ μ¬μ©
    - μμ§ λ°μ€ νλ‘―μ `vert=True` μ΅μ μ¬μ©
    - μν λ°μ€ νλ‘―μ `vert=False` μ΅μ μ¬μ©

  - κ° axe κ°μ²΄μ λ°μ€ νλ‘―μ κ·Έλ¦¬λ `boxplot()` ν¨μλ₯Ό μ¬μ©

```python
# κ·Έλν κ°μ²΄ μμ±
fig = plt.figure(figsize = (15,5))
ax1 = fig.add_subplot(1,2,1)
ax2 = fig.add_subplot(1,2,2)

# λ°μ€ νλ‘― λ§λ€κΈ°
ax1.boxplot(x=[df[df['origin']==1]['mpg'],
               df[df['origin']==2]['mpg'],
               df[df['origin']==3]['mpg']],
            labels=['USA', 'EU', 'JAPAN'])

# κ°λ‘ν λ°μ€ νλ‘― λ§λ€κΈ°
ax2.boxplot(x=[df[df['origin']==1]['mpg'],
               df[df['origin']==2]['mpg'],
               df[df['origin']==3]['mpg']],
            labels=['USA', 'EU', 'JAPAN'],
            vert=False)

plt.show()          
```

![image](https://user-images.githubusercontent.com/100326309/156531628-d4f4ea09-92aa-42cb-b974-3eeb2a279856.png)





---

- `map()`: μ¬λ¬ κ°μ λ°μ΄ν°λ₯Ό νλ²μ λ€λ₯Έ λ°μ΄ν° νμμΌλ‘ λ³ν
  -  map(λ³νν  λ°μ΄ν° νμ, λ°μ΄ν°)
  - ex) `df_4.index = df_4.index.map(int)`
  - ex) `col_years = list(map(str, range(2010, 2018)))`
    - mapν¨μλ κ²°κ³Όκ°μ mapνμμΌλ‘ μΆλ ₯νλ―λ‘ listλ³ν νμ

