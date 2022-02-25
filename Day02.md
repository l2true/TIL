# 2일차 정리🍕



# Github 가입

1. **회원가입**

- [My GitHub](https://github.com/l2true/)
- GitHub 가입 후 bash에서 아이디, 닉네임 확인

```bash
# config 정보 출력
git config --global  --list
```

- Github 설정 변경

  - 프로필 클릭 > Settings > Repositories > (main -> master) 

  

2. **TIL repository 생성 (remote)**

- 원격 저장소를 만드는 것
- New repository > (public)



3. **TIL repository 연결 (remote-local)**

- 원격 저장소와 로컬 저장소 연결

  1. TIL repository > Code > HTTPS url 복사
  2. 컴퓨터의 TIL폴더에서 vscode 열기 ***절대 홈폴더에서 하지 않기!*
  
  ````bash
  # git init을 통해 TIL폴더를 로컬 저장소로 만들기
  git init
  
  # 길 만들기 (등록)
  git remote add origin https://github.com/l2true/TIL.git 
  
  # 조회
  git remote -v 
  ````



4. **README.md**

- 원격 저장소의 대문: 해당 repository의 작성규칙, 마음가짐, 목차 등 작성
  - [참고 github](https://github.com/oypark/TIL)

- TIL폴더에 README.md 파일 생성 > GitHub TIL로 `push`





# 상향식 (init > push)

1. **touch/저장 > add > commit > push**

- 원격 저장소에 로컬 저장소의 커밋들을 올리기 (`push`)

```bash
# 파일 생성
touch Day1.md

# 파일 저장 **필수**
ctrl + s

# stage에 올리기 
git add Day1.md (또는 git add .)

# commit 남기기
git commit -m "add Day1.md" #" "안에는 커밋 메시지

# 내 github로 올리기 (push)
git push origin master
```



2. **gitignore**

- Git이 버전 관리를 하지 못하도록 지정하는 것
- 로컬 저장소에 .gitignore 파일을 만듦 

```bash
touch .gitignore
```

- 만들어진 txt파일에 원하지 않는 파일/폴더를 내용으로 저장 
  - `a.txt`
- 자신의 개발환경에 맞는 코드 복사해서 .gitignore에 붙여넣기 
  - [gitignore 코드 사이트](https://www.toptal.com/developers/gitignore)





# 하향식 (clone, pull)

1. **Clone (복제)**

- 로컬 저장소가 없을 때, 원격 저장소의 버전파일을 똑같이 복제
- 홈폴더에 새폴더 생성 후 vs 열기

```bash
# git clone <url>
git clone https://github.com/l2true/TIL.git 

# 조회
git remote -v 
```

- `git clone` 명령어를 사용하면 길을 새로 만들 필요 없이 한 번에 길이 열리고 복제됨



2. **push <-> pull**

- `pull`: 원격 저장소의 커밋(변경 사항)들을 로컬 저장소에 업데이트 (땡겨주기)

```bash
# pull
git pull origin master
```



3. **Conflict**

-  GitHub 상에서 내용 수정하여 커밋이 생성된 경우, 원격 저장소의 내역과 로컬 저장소의 내역이 달라짐.
- 이때, 로컬 저장소에서 원격으로 `push`할 때 `reject`가 생김
- 로컬과 원격의 conflict -> 먼저 `pull`로 각 버전을 맞춰줘야 함!
  - vs상에서 로컬과 원격의 커밋 달라진 점을 보여주고, 옵션을 선택할 수 있음
  - 옵션: 로컬 내용만 유지 / 원격 내용만 유지 / 둘다 유지
  - 옵션 선택 후 저장(`ctrl+s`)

- 이에 대한 `commit` 남기기 (아직 MERGING 상태)

```bash
# commit을 남겨 merging 완료하기
git commit -m "fix conflict"

# git의 상태 확인: no commit 확인
git status

# git의 commit 내역 확인
git log --oneline
```

- 로컬에서 원격으로 `push`

```bash
# git add를 통해 다시 stage로 올리기 
git add Day1.md

# 원격저장소로 업데이트
git push origin master
```

