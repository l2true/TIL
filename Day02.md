# 2์ผ์ฐจ ์ ๋ฆฌ๐



# Github ๊ฐ์

1. **ํ์๊ฐ์**

- [My GitHub](https://github.com/l2true/)
- GitHub ๊ฐ์ ํ bash์์ ์์ด๋, ๋๋ค์ ํ์ธ

```bash
# config ์ ๋ณด ์ถ๋ ฅ
git config --global  --list
```

- Github ์ค์  ๋ณ๊ฒฝ

  - ํ๋กํ ํด๋ฆญ > Settings > Repositories > (main -> master) 

  

2. **TIL repository ์์ฑ (remote)**

- ์๊ฒฉ ์ ์ฅ์๋ฅผ ๋ง๋๋ ๊ฒ
- New repository > (public)



3. **TIL repository ์ฐ๊ฒฐ (remote-local)**

- ์๊ฒฉ ์ ์ฅ์์ ๋ก์ปฌ ์ ์ฅ์ ์ฐ๊ฒฐ

  1. TIL repository > Code > HTTPS url ๋ณต์ฌ
  2. ์ปดํจํฐ์ TILํด๋์์ vscode ์ด๊ธฐ ***์ ๋ ํํด๋์์ ํ์ง ์๊ธฐ!*
  
  ````bash
  # git init์ ํตํด TILํด๋๋ฅผ ๋ก์ปฌ ์ ์ฅ์๋ก ๋ง๋ค๊ธฐ
  git init
  
  # ๊ธธ ๋ง๋ค๊ธฐ (๋ฑ๋ก)
  git remote add origin https://github.com/l2true/TIL.git 
  
  # ์กฐํ
  git remote -v 
  ````



4. **README.md**

- ์๊ฒฉ ์ ์ฅ์์ ๋๋ฌธ: ํด๋น repository์ ์์ฑ๊ท์น, ๋ง์๊ฐ์ง, ๋ชฉ์ฐจ ๋ฑ ์์ฑ
  - [์ฐธ๊ณ  github](https://github.com/oypark/TIL)

- TILํด๋์ README.md ํ์ผ ์์ฑ > GitHub TIL๋ก `push`





# ์ํฅ์ (init > push)

1. **touch/์ ์ฅ > add > commit > push**

- ์๊ฒฉ ์ ์ฅ์์ ๋ก์ปฌ ์ ์ฅ์์ ์ปค๋ฐ๋ค์ ์ฌ๋ฆฌ๊ธฐ (`push`)

```bash
# ํ์ผ ์์ฑ
touch Day1.md

# ํ์ผ ์ ์ฅ **ํ์**
ctrl + s

# stage์ ์ฌ๋ฆฌ๊ธฐ 
git add Day1.md (๋๋ git add .)

# commit ๋จ๊ธฐ๊ธฐ
git commit -m "add Day1.md" #" "์์๋ ์ปค๋ฐ ๋ฉ์์ง

# ๋ด github๋ก ์ฌ๋ฆฌ๊ธฐ (push)
git push origin master
```



2. **gitignore**

- Git์ด ๋ฒ์  ๊ด๋ฆฌ๋ฅผ ํ์ง ๋ชปํ๋๋ก ์ง์ ํ๋ ๊ฒ
- ๋ก์ปฌ ์ ์ฅ์์ .gitignore ํ์ผ์ ๋ง๋ฆ 

```bash
touch .gitignore
```

- ๋ง๋ค์ด์ง txtํ์ผ์ ์ํ์ง ์๋ ํ์ผ/ํด๋๋ฅผ ๋ด์ฉ์ผ๋ก ์ ์ฅ 
  - `a.txt`
- ์์ ์ ๊ฐ๋ฐํ๊ฒฝ์ ๋ง๋ ์ฝ๋ ๋ณต์ฌํด์ .gitignore์ ๋ถ์ฌ๋ฃ๊ธฐ 
  - [gitignore ์ฝ๋ ์ฌ์ดํธ](https://www.toptal.com/developers/gitignore)





# ํํฅ์ (clone, pull)

1. **Clone (๋ณต์ )**

- ๋ก์ปฌ ์ ์ฅ์๊ฐ ์์ ๋, ์๊ฒฉ ์ ์ฅ์์ ๋ฒ์ ํ์ผ์ ๋๊ฐ์ด ๋ณต์ 
- ํํด๋์ ์ํด๋ ์์ฑ ํ vs ์ด๊ธฐ

```bash
# git clone <url>
git clone https://github.com/l2true/TIL.git 

# ์กฐํ
git remote -v 
```

- `git clone` ๋ช๋ น์ด๋ฅผ ์ฌ์ฉํ๋ฉด ๊ธธ์ ์๋ก ๋ง๋ค ํ์ ์์ด ํ ๋ฒ์ ๊ธธ์ด ์ด๋ฆฌ๊ณ  ๋ณต์ ๋จ



2. **push <-> pull**

- `pull`: ์๊ฒฉ ์ ์ฅ์์ ์ปค๋ฐ(๋ณ๊ฒฝ ์ฌํญ)๋ค์ ๋ก์ปฌ ์ ์ฅ์์ ์๋ฐ์ดํธ (๋ก๊ฒจ์ฃผ๊ธฐ)

```bash
# pull
git pull origin master
```



3. **Conflict**

-  GitHub ์์์ ๋ด์ฉ ์์ ํ์ฌ ์ปค๋ฐ์ด ์์ฑ๋ ๊ฒฝ์ฐ, ์๊ฒฉ ์ ์ฅ์์ ๋ด์ญ๊ณผ ๋ก์ปฌ ์ ์ฅ์์ ๋ด์ญ์ด ๋ฌ๋ผ์ง.
- ์ด๋, ๋ก์ปฌ ์ ์ฅ์์์ ์๊ฒฉ์ผ๋ก `push`ํ  ๋ `reject`๊ฐ ์๊น
- ๋ก์ปฌ๊ณผ ์๊ฒฉ์ conflict -> ๋จผ์  `pull`๋ก ๊ฐ ๋ฒ์ ์ ๋ง์ถฐ์ค์ผ ํจ!
  - vs์์์ ๋ก์ปฌ๊ณผ ์๊ฒฉ์ ์ปค๋ฐ ๋ฌ๋ผ์ง ์ ์ ๋ณด์ฌ์ฃผ๊ณ , ์ต์์ ์ ํํ  ์ ์์
  - ์ต์: ๋ก์ปฌ ๋ด์ฉ๋ง ์ ์ง / ์๊ฒฉ ๋ด์ฉ๋ง ์ ์ง / ๋๋ค ์ ์ง
  - ์ต์ ์ ํ ํ ์ ์ฅ(`ctrl+s`)

- ์ด์ ๋ํ `commit` ๋จ๊ธฐ๊ธฐ (์์ง MERGING ์ํ)

```bash
# commit์ ๋จ๊ฒจ merging ์๋ฃํ๊ธฐ
git commit -m "fix conflict"

# git์ ์ํ ํ์ธ: no commit ํ์ธ
git status

# git์ commit ๋ด์ญ ํ์ธ
git log --oneline
```

- ๋ก์ปฌ์์ ์๊ฒฉ์ผ๋ก `push`

```bash
# git add๋ฅผ ํตํด ๋ค์ stage๋ก ์ฌ๋ฆฌ๊ธฐ 
git add Day1.md

# ์๊ฒฉ์ ์ฅ์๋ก ์๋ฐ์ดํธ
git push origin master
```

