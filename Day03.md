# 3์ผ์ฐจ ์ ๋ฆฌ ๐



## Branch

- branch: ๋๋ญ๊ฐ์ง

1. **๋ธ๋์น ์์ฑ**

```bash
# ๋ธ๋์น ๋ชฉ๋ก ํ์ธ
git branch -> default: master

# ๋ธ๋์น ์์ฑ
git branch ์ ๊ท ๋ธ๋์น๋ช
```



2. **๋ธ๋์น ์ด๋**

```bash
# ๋ธ๋์น ์ด๋
git switch ๋ค๋ฅธ ๋ธ๋์น๋ช  # git log๋ฅผ ํตํด ํ์ธ ๊ฐ๋ฅ

# ๋ค๋ฅธ ๋ธ๋์น๋ฅผ ๋ง๋ค๋ฉด์ ์ด๋
git switch -c ๋ค๋ฅธ ๋ธ๋์น๋ช

# ๋ธ๋์น๋ฅผ ์ญ์ 
git branch -d ๋ค๋ฅธ ๋ธ๋์น๋ช
git branch -D ๋ค๋ฅธ ๋ธ๋์น๋ช # ๊ฐ์ ์ญ์  ์ต์

# ๋ชจ๋  ๋ธ๋์น ์กฐํ
git log --oneline --all
git log --oneline --all --graph
```



3. **๋ธ๋์น ํฉ์น๊ธฐ** (merge)

```bash
# ๋ธ๋์น ๋ณํฉ
git merge ๋ณํฉํ  ๋ธ๋์น๋ช

# ๋ณํฉ๋ ๋ค๋ฅธ ๋ธ๋ฐ์น๋ ์ญ์ 
git branch -d ๋ค๋ฅธ ๋ธ๋์น๋ช
```



## Workflow

1. **Shared repository model**

- ์๊ฒฉ ์ ์ฅ์ ์์ ๊ถ์ด ์๋ ๊ฒฝ์ฐ (๋ณธ์ธ ์์  or collaborator)

- ์๊ฒฉ ์ ์ฅ์๋ฅผ ๋ก์ปฌ์ `clone`

- ๋ก์ปฌ ์ ์ฅ์์์ ์์ ํ ์๊ฒฉ ์ ์ฅ์์ `push`

  - [ ] ๊ธฐ๋ฅ ์ถ๊ฐ๋ฅผ ์ํด branch ์์ฑ ๋ฐ ๊ธฐ๋ฅ ๊ตฌํ
  - [ ] ์๊ฒฉ ์ ์ฅ์์ ํด๋น ๋ธ๋์น๋ฅผ `push`
  - [ ] pull request๋ฅผ ํตํด ๋ธ๋์น๋ฅผ master์ ๋ฐ์ํ  ๊ฒ์ ์์ฒญ
  - [ ] ๋ณํฉ ์๋ฃ๋ ๋ธ๋์น๋ ์ญ์ 

- ์๊ฒฉ ์ ์ฅ์์ ๋ด์ฉ์ ๋ก์ปฌ์ master ๋ธ๋์น์ ์๋ฐ์ดํธํ๊ธฐ

  - [ ] ๋ค์ ๋ก์ปฌ์ master ๋ธ๋์น๋ก ์ด๋ 

  - [ ] ์๊ฒฉ ์ ์ฅ์์ ๋ฐ์๋ master ๋ด์ฉ์ ๋ก์ปฌ๋ก ๋ฐ์์ค๊ธฐ
  - [ ] ๋ณํฉ ์๋ฃ๋ master ๋ธ๋์น๋ฅผ ๋ฐ์์ผ๋ฏ๋ก, ๊ธฐ์กด ๋ก์ปฌ ๋ธ๋์น๋ ์ญ์ 



2. **Forking Workflow**

- ๊ถํ์ด ์๋ ์๊ฒฉ ์ ์ฅ์๋ฅผ ๋ด ๋ก์ปฌ์์ ์ฌ์ฉํ๋ ๋ฐฉ๋ฒ

- ์๊ฒฉ ์ ์ฅ์์์ ํฌํฌ๋ก ์ฝ ์ฐ์ด์ ๋ก์ปฌ์ `clone`(๋ณต์ )

  - [ ] ๋ค๋ฅธ ์ฌ๋์ GitHub์์ ํ๋ฉด ์ฐ์ธก ์๋จ `Fork` ํด๋ฆญ
  - [ ] ๋ด ๋ ํฌ์งํฐ๋ฆฌ์์ ์ฝ๋ `url` ๋ณต์ฌ
  - [ ] bash์ฐฝ์์ `clone`

  ```bash
  # ๋ณต์ 
  git clone https://github.com/l2true/acrostic-poem.git
  
  # ๋ณต์ ๋ ํด๋๋ก ์ด๋ํ์ฌ master ํ์ธ
  cd ํด๋๋ช
  
  # VS ์ด๊ธฐ
  code .
  ```

- ๋ก์ปฌ ์ ์ฅ์์์ ์์ ํ ์๊ฒฉ ์ ์ฅ์์ `push`

  - [ ] ๊ธฐ๋ฅ ์ถ๊ฐ๋ฅผ ์ํด branch ์์ฑ ๋ฐ ๊ธฐ๋ฅ ๊ตฌํ

  ```bash
  # ๋ธ๋์น ์์ฑ ํ ์ด๋
  git switch -c ๋ธ๋์น๋ช
  
  # ๊ธฐ๋ฅ ๊ตฌํ ํ ์ ์ฅ
  crtl + s
  ```

  - [ ] ์๊ฒฉ ์ ์ฅ์๋ก  `push` 

  ```bash
  # ์คํ์ด์ง ์ฌ๋ฆฌ๊ธฐ
  git add ํ์ผ๋ช
  
  # commit ๋จ๊ธฐ๊ธฐ
  git commit -m "์ปค๋ฐ ๋ฉ์์ง"
  
  # push
  git push origin ๋ธ๋์น๋ช
  ```

  - [ ] GitHub์์ ์ด๋ก์ ๋ฒํผ `pull request` ํด๋ฆญํ์ฌ ์์ฒญ ๋ณด๋ด๊ธฐ



---

- **git diff**

  - ์ปค๋ฐ๋ค ์ฌ์ด ๋ณ๊ฒฝ์ฌํญ์ ์ฐจ์ด๋ฅผ ๋ณด์ฌ์ฃผ๋ ๋ช๋ น์ด

    ```bash
    # ๊ฐ ์ปค๋ฐ๋ค์ ํด์ฌ๊ฐ ํ์ธ
    git log --oneline
    
    # log๋ฅผ ํตํด ํ์ธํ ํด์ฌ๊ฐ์ผ๋ก ๋น๊ต
    git diff ํด์๊ฐ ํด์๊ฐ (๋น๊ตํ  ๋์ 2๊ฐ) 
    ```

    

- **commit์ฐฝ์ VIM์ด ์๋ VScode๋ก ๋ฐ๊พธ๊ธฐ**

  - ํํด๋์์ bash์ฐฝ ์ด๊ธฐ 

    ```bash
    # ์ค์  ๋ณ๊ฒฝ
    git config --global core.editor "code --wait"
    
    # list ๋ณด๊ธฐ
    git config --global --list
    ```



- **๊นํ๋ธ ํ๋กํ ๊พธ๋ฐ ๋ ์ฐธ๊ณ **
  - https://github.com/kautukkundan/Awesome-Profile-README-templates/blob/master/dynamic-realtime/quadrified.md
  - https://github.com/simonw
  - https://github.com/jlengstorf
  - https://github.com/katmeister
  - https://github.com/pifafu