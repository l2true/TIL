# 3일차 정리 🍕



## Branch

- branch: 나뭇가지

1. **브랜치 생성**

```bash
# 브랜치 목록 확인
git branch -> default: master

# 브랜치 생성
git branch 신규 브랜치명
```



2. **브랜치 이동**

```bash
# 브랜치 이동
git switch 다른 브랜치명  # git log를 통해 확인 가능

# 다른 브랜치를 만들면서 이동
git switch -c 다른 브랜치명

# 브랜치를 삭제
git branch -d 다른 브랜치명
git branch -D 다른 브랜치명 # 강제삭제 옵션

# 모든 브랜치 조회
git log --oneline --all
git log --oneline --all --graph
```



3. **브랜치 합치기** (merge)

```bash
# 브랜치 병합
git merge 병합할 브랜치명

# 병합된 다른 브런치는 삭제
git branch -d 다른 브랜치명
```



## Workflow

1. **Shared repository model**

- 원격 저장소 소유권이 있는 경우 (본인 소유 or collaborator)

- 원격 저장소를 로컬에 `clone`

- 로컬 저장소에서 작업 후 원격 저장소에 `push`

  - [ ] 기능 추가를 위해 branch 생성 및 기능 구현
  - [ ] 원격 저장소에 해당 브랜치를 `push`
  - [ ] pull request를 통해 브랜치를 master에 반영할 것을 요청
  - [ ] 병합 완료된 브랜치는 삭제

- 원격 저장소의 내용을 로컬의 master 브랜치에 업데이트하기

  - [ ] 다시 로컬의 master 브랜치로 이동 

  - [ ] 원격 저장소에 반영된 master 내용을 로컬로 받아오기
  - [ ] 병합 완료된 master 브랜치를 받았으므로, 기존 로컬 브랜치는 삭제



2. **Forking Workflow**

- 권한이 없는 원격 저장소를 내 로컬에서 사용하는 방법

- 원격 저장소에서 포크로 콕 찍어서 로컬에 `clone`(복제)

  - [ ] 다른 사람의 GitHub에서 화면 우측 상단 `Fork` 클릭
  - [ ] 내 레포지터리에서 코드 `url` 복사
  - [ ] bash창에서 `clone`

  ```bash
  # 복제
  git clone https://github.com/l2true/acrostic-poem.git
  
  # 복제된 폴더로 이동하여 master 확인
  cd 폴더명
  
  # VS 열기
  code .
  ```

- 로컬 저장소에서 작업 후 원격 저장소에 `push`

  - [ ] 기능 추가를 위해 branch 생성 및 기능 구현

  ```bash
  # 브랜치 생성 후 이동
  git switch -c 브랜치명
  
  # 기능 구현 후 저장
  crtl + s
  ```

  - [ ] 원격 저장소로  `push` 

  ```bash
  # 스테이지 올리기
  git add 파일명
  
  # commit 남기기
  git commit -m "커밋 메시지"
  
  # push
  git push origin 브랜치명
  ```

  - [ ] GitHub에서 초록색 버튼 `pull request` 클릭하여 요청 보내기



---

- **git diff**

  - 커밋들 사이 변경사항의 차이를 보여주는 명령어

    ```bash
    # 각 커밋들의 해쉬값 확인
    git log --oneline
    
    # log를 통해 확인한 해쉬값으로 비교
    git diff 해시값 해시값 (비교할 대상 2개) 
    ```

    

- **commit창을 VIM이 아닌 VScode로 바꾸기**

  - 홈폴더에서 bash창 열기 

    ```bash
    # 설정 변경
    git config --global core.editor "code --wait"
    
    # list 보기
    git config --global --list
    ```



- **깃허브 프로필 꾸밀 때 참고**
  - https://github.com/kautukkundan/Awesome-Profile-README-templates/blob/master/dynamic-realtime/quadrified.md
  - https://github.com/simonw
  - https://github.com/jlengstorf
  - https://github.com/katmeister
  - https://github.com/pifafu