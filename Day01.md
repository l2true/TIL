# CLI

- CLI VS GUL
- 커맨드라인 명령어

```python
#디렉토리 생성
mkdir

#디렉토리 이동
cd

#파일 생성
touch

#디렉토리 안 리스트 확인
ls

#제거
rm
-r 옵션: 재귀적
--r 옵션: 강제 삭제

#이동/이름 변경
mv

#현재의 경로를 보여줌
pwd

#화면 깨끗이/스크롤 올리기
clear
ctrl + l
```



# 마크다운

- 마크다운 역할
  - 마크업: html -> 개발자 도구로 확인 (태그)
  - 마크다운: 경량화된 마크업 언어
- 마크다운 문법

1. 제목: # ~ ######
2. 목록: -, *, +
3. 들여쓰기: `tab`, `shift + tab`
4. 강조
   - *기울임*
   - **굵게**
   - ***기울이고 굵게***

5. 코드

   - `인라인`: '한줄코드' 백틱으로 묶기
   - 코드블럭: 여러줄 코드를 백틱 3개로 묶기

   ```python
   print('hello git!')
   ```

6. 링크: [표시할 텍스트](url)

7. 이미지

   - ![대체 텍스트](url)
   - 복사 붙여넣기 할 때: assets으로 복사

8. 구분선: ---

9. > 인용1
   >
   > > 인용2

10. 표: ctrl + t

    |      |      |      |
    | ---- | ---- | ---- |
    |      |      |      |
    |      |      |      |
    |      |      |      |



---



# git 기초

- git의 3공간
  - 분장실, 무대, 사진 촬영본
  - working directory, staging area, commits
- file 기준
  - git init
    - 유의사항: 맨 처음 1회, 절대 홈폴더에서 하지 않는다.
    - git init한 폴더의 하위폴더에서 절대 git init하지 않는다.
  - git add
  - git commit -m "메시지"
  - git status: 파일 상태를 확인
  - git log: 커밋 내역 확인
    - --onleline: 한줄출력

- git 초기 설정

  - git config

  ```python
  git config --global user.name "유저명"
  git config --global user.email "유저 이메일" # 깃허브에서 사용
  ```

  

---

