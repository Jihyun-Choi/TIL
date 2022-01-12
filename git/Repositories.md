# Git에서 Repository 생성하기


### Github에서 Repository 생성하기

페이지 우측 상단의 `+` 를 누른 후 `New repository`를 누른다.
 
**필수적으로 작성해야 하는 것** : Repository name에 이름 작성하기

다른 사람들이 볼 수 있는 공개적인 레포지토리로 만든다면, Public을 선택하고
<br/>
나만 볼 수 있는 비공개적인 레포지토리로 만든다면, Private을 선택하면 된다.

<br/>
<br/>

또한 레포지토리를 생성 시 자동적으로 README file을 생성하고싶다면 `Add a README file`를 체크하면 된다.
추후에 README file을 추가할 수 있으므로 체크해도 되고 안해도 된다.
 

<br/>
<br/>
<br/>
### 생성한 Repository와 연결하기

진행중인 프로젝트 터미널에서 아래의 코드들을 순서대로 입력하면 된다.

```
    git init
    git status
    git add .
    git commit -m "[커밋메세지]"
    git push origin master
```

<br/>
[추가적으로 더 많은 명령어와 설명이 궁금하다면 ...](https://github.com/Jihyun-Choi/TIL/blob/master/git/command.md)