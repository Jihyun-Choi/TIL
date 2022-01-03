# Git 명령어 정리


### 기본적인 git 사용
`git init`
git을 활성화시키기 위한 명령어, 현재 파일에 새로운 git 지역저장소 생성

`git status`
git의 상태를 확인

`git add .`
git에 모든 파일을 스테이지에 올림

`git commit -m "[커밋메세지]"`
[커밋메세지]를 붙여서 커밋


`git push origin master`
원격저장소로 푸시하기

<br/>

### 원격저장소 연결

`git remote -v`
git 레파지토리 원격저장소 확인

`git remote add (원격저장소이름 (origin)) (깃주소)`
git 원격 저장소 연결

<br/>

### 브랜치
`git branch`
브랜치 조회하기

`git branch [브랜치명]`
새로운 브랜치 [브랜치명]을 생성

`git checkout [브랜치명]`
[브랜치명]으로 체크아웃

git checkout -b [브랜치명]  # 브랜치만들고 바로 이동

`git branch -d [브랜치명]`
브랜치 삭제

<br/>

### 수정하기
`git reset —hard HEAD`
가장 최근에 한 커밋으로 작업 되돌리기
