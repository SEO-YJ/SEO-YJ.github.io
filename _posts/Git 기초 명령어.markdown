---
layout: post
title:  "Git 기초 명령어"
date:   2022-04-21 18:47:28 +0900
categories: Git알못을 위한 깃린이코스(Git, Github 실습위주) 정리
---
# Git 설치 (Window, Mac)
## Git 로컬에 설치 되어있는지 확인 방법
맥북
1. Command + space 클릭
2. Spotlight에서 '터미널' 검색
3. git --version 입력 
내 로컬 결과: git version 2.30.1 (Apple Git-130)

## 로컬에 설치 되어있지 않은 경우(다운로드 방법)
1. 구글 브라우저 열기
2. git 홈페이지 검색
3. 들어가서 Git 다운로드
4. 설치 완료 후 Command + space로 spotlight 열어서 터미널 열기
5. git --version 설치 확인
6. 잘 설치되었는지 확인
7. git config --global init.defaultBranch main
( 최근에 메인 브랜치가 master -> main으로 변경되었다.
그에 대한 에러를 방지하기 위해서 위 명령어를 입력해 주면 된다.
딱히, 실행결과는 출력되지 않는다.)

# git config --global
Git을 로컬에 설치 후, 맨 처음에 입력해야 할 명령어
## 효과
1. User name을 로컬에 지정해준다.
2. User email을 로컬에 지정해준다.

내 생각
아마, Github의 name과 email을 연동?시켜 주는 과정이 아닐까...?
흠,,,
강사님께서는 지금은 본인이 가장 좋아하는 이름과 이메일을 넣어주라고 하셨다.
아직 Github 회원가입 과정은 거치지 않아서 임시로 지정해주는 것 아닐까.,..,.,????

## git config 뒤에 'global'이 붙는 이유
앞으로 이 로컬에서 수행하는 과정은 모두 
지정한 User name으로 수행할 것이다. global하게 할 것이다라는 뜻
아직은 감이 잡히지 않는다...

## 터미널에 명령어를 직접 입력해보자.
이름  세팅: git config --global user.name "YUJUN SEO"
이메일 세팅: git config --global user.email "yujun@~"
세팅 확인: git config --list
(user.name과 user.email을 확인 할 수 있다.
현재 내 맥북은 깃허브 이름과 이메일로 세팅되어있다!)

## 영어 단어 config
config는 configuration의 약자로 사용하는 것 같다.
컴퓨터 분야에서 단어의 뜻은 '환경 설정'이다.
위 명령어를 보면 
git config --global user.name "YUJUN SEO"
를 내 방식대로 해석해보면
=> git의 '모든 로컬'에서 '사용자의 이름'을 "YUJUN SEO"로 "환경 설정"해준다! 라고 볼 수 있을 것 같다.

# CMD(Terminal) 기본 명령어 -> CMD랑 친해지면 좋다.
## 폴더 내 파일들 확인 명령어
윈도우: dir
맥: ls
### 효과
폴더 내의 모든 파일들의 이름이 나온다. 
현재 폴더에서 다른 폴더로 이동할 때 용이하다.

## 폴더 내 다른 파일로 이동하는 명령어
윈도우, 맥: cd "파일명"
### 효과
1. ls로 현재 폴더 내에 어떤 파일들이 있는지 확인한다.
2. 이동할 파일의 이름을 확인한다.
3. cd "파일명"을 통해 해당 파일로 이동한다.

## 폴더 외부로 나가는 명령어
윈도우, 맥: cd ..

## 사용자의 '루트'폴더에 git 폴더 만들기
### 루트 폴더란?
터미널 실행 시 맨 처음의 위치
### 효과
cd 명령어 한 번으로 git 폴더들 내부로 이동해 파일들을 관리할 수 있다.

## 폴더 내부에 폴더를 만드는, 제거하는 명령어
폴더를 만드는 경우: 윈도우, 맥: mkdir "만들 폴더명"
폴더를 제거하는 경우: 윈도우, 맥: rmdir "제거할 폴더명"

내 생각
폴더를 만드는 경우는 "make directory"의 약자인 것 같고,
폴더를 제거하는 경우는 "remove directory"의 약자인 것 같다.

# git init, git add, git commit, git log의 이해
## 각각의 명령어들의 개념을 설명
### 현재까지 알고 있는 위 명령어 개념 정리
git init: 폴더 안에 git 파일을 넣어 git으로 관리하게 해준다.
git add: 현재까지 수행한 저장된 파일들을 임시의 공간에 저장한다.
git commit: git add를 통해 임시로 저장된 파일들을 버전으로 관리하여 저장한다.
git log: 현재까지 git commit 명령어로 버전 관리된 파일들을 리스트로 확인할 수 있다.

## 버전관리를 사진찍기로 비유해 보자.
사진찍는 과정의 요소들을 생각해보자.
1. 사진사
2. 모여있는 사람들
3. 찍은 사진
4. 앨범

### git init
역할: 사진사
=> 한 프로젝트를 관리할 때 최초 1회만 명령

### git add
역할: 모여있는 사람들
=> 사진에 찍힐 '코드파일'들을 모아준다.
=> 찍을 때마다, 모이는 '코드파일'들이 다를 수 있으므로, 
사진을 찍을 때마다 명령해주어야 한다.

### git commit
역할: 찍은 사진
=> 모인 '코드파일'들을 '찰칵'하고 찍게 된다.
=> 당연하게도 매번 명령

### git log
역할: 앨범
=> 찍은 사진들을 볼 수 있는 앨범같은 것

# 로컬에서의 형상관리 with 메모장 (init, add, commit, status, log, reset)
## git을 명령어로 다뤄볼 것 이다.
### 메모장을 이용한 테스트!
순서
1. 프로젝트를 관리할 폴더 생성(cmd + space(spotlight open) -> terminal -> cd desktop -> mkdir inflearnTest)
2. git init 
   사진사를 고용(git init)
3. .git 숨김 폴더 생성(이게 아마 사진사의 역할을 하는 폴더인 듯)
4. git 버전관리 툴에 버전관리할 파일들을 생성 (여기서는 메모장을 가지고 테스트, .git 폴더와 '동일한 위치'에 생성!)
5. (맥에서는 cmd + space -> text editor(텍스트 편집기)를 눌러서 파일을 생성할 수 있다.)
6. 현재 상태는 파일들(사람들)은 있지만, 사람들이 모여있지 않고 중구난방 흩어져 있는 상태!
7. git status
  git status 명령어로 현재 프로젝트 폴더 내부의 파일들의 '상태'를 확인할 수 있다.
  Untracked files:
  (use "git add <file>..." to include in what will be committed) 
  .DS_Store
    inflearn-gitTest1.rtf
    inflearn-gitTest2.rtf
  "commit할 것들을 포함하는 git add <file> 명령어를 사용해라!"
  빨간 글씨로 현재 프로젝트 내부의 폴더들이 add 되어있지 않다는 것을 알려주고 있다.
8. 흩어져 있는 파일들을 모아주는 git add 명령어를 사용하자.
9. git add .
    '.git 폴더가 속한 폴더 내부의 파일들 전부 모여!'라는 명령어이다.
    그러면, git add . 대신에 git add <file명>을 통해, 특정 파일들만 모여!라고도 할 수 있겠다.
    
    Q. git add <file명>으로 특정 파일만 add 시켜보려고 했는데 안 되었다.
    궁금하여 찾아보았더니, file명의 뒤에 .rtf 까지 입력해주어야 했다.
    
    * 특정 파일 add 전 상태
    
    Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
    new file:   .DS_Store
    new file:   inflearn-gitTest1.rtf
    new file:   inflearn-gitTest2.rtf

Untracked files:
  (use "git add <file>..." to include in what will be committed)
    inflearn-gitTest3.rtf
    inflearn-gitTest4.rtf
    
    * 특정 파일을 add
    git add inflearn-gitTest3.rtf
    git status
    
    * 특정 파일 add 후 상태
    Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
    new file:   .DS_Store
    new file:   inflearn-gitTest1.rtf
    new file:   inflearn-gitTest2.rtf
    new file:   inflearn-gitTest3.rtf

Untracked files:
  (use "git add <file>..." to include in what will be committed)
    inflearn-gitTest4.rtf
    
    관련 링크
    https://herojoon-dev.tistory.com/51

10. git rm --cached <file>
    git add를 통해 사진찍을 준비를 한 파일들을 add 상태를 제거하는 명령어이다.
    git add <file명>처럼 .rtf와 같이 확장자까지 명시해주어야 한다.
    git rm --cached .을 하면 git add .와는 다르게 안된다.

11. git commit -m "커밋명"
    
    사진찍을 모든 사람들을 git add . 명령어로 모아놨으니,
    git commit -m "커밋명"을 통해, 사진을 찍었다.
    
    * 결과
    [main (root-commit) f84cb63] initial commit
    5 files changed, 32 insertions(+)
    create mode 100644 .DS_Store
    create mode 100644 inflearn-gitTest1.rtf
    create mode 100644 inflearn-gitTest2.rtf
    create mode 100644 inflearn-gitTest3.rtf
    create mode 100644 inflearn-gitTest4.rtf
    
    * 나만의 해석
    [main (root-commit) f84cb63] initial commit
    
    1) main 루트에 f84cb63이라는 위치에 커밋이 생성되었다.
    2) 커밋의 이름은 'initial commit'이다.
    
    5 files changed, 32 insertions(+)
    create mode 100644 .DS_Store
    create mode 100644 inflearn-gitTest1.rtf
    create mode 100644 inflearn-gitTest2.rtf
    create mode 100644 inflearn-gitTest3.rtf
    create mode 100644 inflearn-gitTest4.rtf
    
    1) 5개의 파일들이 바뀌었다.
    2) insertion은 삽입되었다는 것 같은데, 왜 32인지는 모르겠다.
    
    * initial commit
    보통 프로젝트의 '최초 커밋'을 할 때, 많이들 사용하는 커밋명이다.
    
12. git log
    전 강의에서 아마 '앨범'과 같은 기능을 하는 명령어라고 알고 있다.
    git log 명령어를 통해 프로젝트의 커밋들을 확인해 볼 수 있다.
    
    * 결과
    commit f84cb631a1556c25d12c91b42208ced7cc8bc6df (HEAD -> main)
    Author: 이름 <이메일>
    Date:   Mon May 2 14:58:07 2022 +0900

    initial commit
    
    * 나만의 해석
    commit f84cb631a1556c25d12c91b42208ced7cc8bc6df (HEAD -> main)
    
    1) git commit -m "initial commit"을 하였을 때, 
    [main (root-commit) f84cb63] initial commit
    위치에 생성되었다고 나와있는데, f84cb63은 
        f84cb631a1556c25d12c91b42208ced7cc8bc6df 이게 생략된 것이었다.
    
    Author: 이름 <이메일>
    Date:   Mon May 2 14:58:07 2022 +0900
    
    1) 처음에 로컬에 git을 다운로드 받고 세팅을 할 때,
    이름  세팅: git config --global user.name "YUJUN SEO"
    이메일 세팅: git config --global user.email "yujun@~"
    위 명령들로 이름, 이메일을 세팅해주었는데,
    git log를 확인해보니, Author(작성자)에 세팅한 개인정보들이 나오는 것을 알 수 있다.
    2) 날짜도 나온다.

    initial commit
    
13. 파일의 내용을 변경해보고, git status로 확인해보자
    On branch main
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
    modified:   inflearn-gitTest4.rtf
    
    친절하게도, inflearn-gitTest4.rtf 파일의 내용이 수정되었다는 것을 확인할 수 있다.
    그리고, 
    git add <file> 명령을 통해, add 상태로 업데이트를 진행하던가
    git restore <file> 명령을 통해, 파일 변경을 제거할 수도 있다.
    
14. git restore
    git restore 명령어를 사용하면, 
    수정한 파일을 다시 add 한 전 상태로 변경할 수 있다.
    
    * 나만의 해석
    1. 프로젝트의 파일들을 테스트 해보고 테스트가 성공적으로 실행되면, git add . -> git commit ""을 진행한다.
    2. 테스트가 실패하게 되면, 다시 add 상태로 돌리기 위해 git restore <file>을 하여, add 상태로 돌린다.
    3. git restore은 git commit 전 (사진을 찍기 전)에만 가능하다.
    
15. git reset --hard 상태(ex> f84cb631a1556c25d12c91b42208ced7cc8bc6df)
    그러면, git commit -m "커밋명" 명령을 통해, 새로운 커밋이 생성되었는데,
    다시, git restore 처럼 파일을 전으로 돌리고 싶을 경우에는 어떻게 해야할까?
    이떄, git reset --hard를 이용한다.
    git reset --hard 상태 
    명령을 진행하면, 전 커밋 상태로 이동할 수 있으며, 앞의 커밋은 '제거'된다.
    
    git reset --hard f84cb631a1556c25d12c91b42208ced7cc8bc6df
    * reset 전
    commit 32ee611877a9b2d07a76f226d7e87814d6551117 (HEAD -> main)
    Author: 이름 <이메일>
    Date:   Mon May 2 15:19:55 2022 +0900

    modify one file

    commit f84cb631a1556c25d12c91b42208ced7cc8bc6df
    Author: 이름 <이메일>    
    Date:   Mon May 2 14:58:07 2022 +0900

    initial commit
    
    * reset 후
    HEAD is now at f84cb63 initial commit
    
    commit f84cb631a1556c25d12c91b42208ced7cc8bc6df (HEAD -> main)
    Author: 이름 <이메일>
    Date:   Mon May 2 14:58:07 2022 +0900

    Q. 그러면, git reset --hard 상태 명령어로 전 커밋 상태로 이동을 하면,
    다시, 앞의 커밋으로는 이동이 안되냐?
    
    A. github를 배우면 알 수 있습니다.
    
16. git reset --hard
    add, commit까지 다 한후에,
    막 파일들을 수정하였는데, 파일들을 커밋한 상태로 원상복구하고 싶을 경우에
    git reset --hard만 입력해주면 커밋한 상태로 복구된다.
    
    
## 명령어 정리
### git --version
: 현재 로컬에 설치된 git 버전관리 툴의 버전을 확인할 수 있는 명령어

### git config --global init.defaultBranch main
: git의 root 브랜치가 master -> main으로 변경되었으므로,
main으로 초기에 세팅해주는 명령어
1회만 명령해주면 된다.

### git config --global user.name "YUJUN SEO"
: 현재 로컬의 git의 이름을 환경 설정 해주는 명령어

### git config --global user.email "yujun@~"
: 현재 로컬의 git의 이메일을 환경 설정 해주는 명령어

### git config --list
: 환경 설정 세팅을 확인하는 명령어

### git init
: 폴더 안에 git 파일을 넣어 git으로 관리해주는 명령어
(사진사 고용)
* 강의 자료
1) .git 폴더 생성
2) .git 폴더가 생성된 폴더는 git이 관리하기 시작함

### git add .
: 현재까지 수행한 저장된 파일들을 임시의 공간에 '모두' 저장하는 명령어
( 사진에 찍힐 사람들을 한꺼번에 모으는 명령어)
* 강의 자료
1) 모든 파일 스테이징 (말이 어렵지만 '추적'을 시작한다라고 보면 된다.)

### git add <file명>
: 현재까지 수행한 저장된 파일 중 '특정 파일'을 임시의 공간에 저장하는 명령어
( 사진에 찍힐 사람들 중 특정 사람들을 골라 모으는 명령어)

### git commit -m "message"
: git add를 통해 임시로 저장된 파일들을 버전으로 관리하여 저장하는 명령어
( 사진의 이름, 저장된 파일들, 로컬에 저장된 환경 상태, 날짜 등을 확인 가능)
* 강의 자료
1) message 이름으로 현재 추적하고 있는 코드들을 '찰칵'

### git log
: 현재까지 git commit 명령어로 버전 관리된 파일들을 리스트로 확인하는 명령어
( 앨범)
* 강의 자료
1) 커밋 로그를 확인

### git status
: 프로젝트 내부의 파일들이 '임시의 공간'에 저장되었는지 확인하는 명령어
* 강의 자료
1) 현재 git의 상태를 보여줌

### git rm --cached <file>
: git add 명령어를 통해 임시의 공간에 저장된 파일들 중, 
특정 파일을 선택해 임시의 공간에서 제거하는 명령어
(너 나와봐!)

### git restore
: git add를 통해 임시의 공간에 파일을 저장해 놓았는데,
저장한 파일을 수정하였다가 다시 add를 명령했던 상태로 돌아가고 싶을 때, 사용하는 명령어

### git reset --hard 커밋해쉬코드(번호)
: 이전 commit으로 되돌리고 싶을때 사용하는 명령어
* 강의 자료
1) 커밋 번호에 해당하는 커밋으로 코드를 롤백

### git reset --hard
: commit을 한 후에, 파일들을 수정하던 중 다시 이전 'commit'의 상태로 파일들을 되돌리고 싶을 때 사용하는 명령어

    
