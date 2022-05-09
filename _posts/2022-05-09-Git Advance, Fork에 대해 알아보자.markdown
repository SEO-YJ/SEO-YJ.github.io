---
layout: post
title:  "Git Advance, Fork에 대해 알아보자"
date:   2022-05-09 17:06:00 +0900
categories: Git알못을 위한 깃린이코스(Git, Github 실습위주) 정리
---
# 협업 하는 방식 두번째, Fork
## fork 란?
fork로 찍어서 가져온다.
= 남의 리포지토리에서 '그대로 복제 Fork'해서 내 리포지토리로 가져온다.
가져온 리포지토리를
내 로컬로 '클론(clone)'해서 여기서 작업해서 푸시를 한다.
내 리포지토리에만 반영이 되어있는 변경사항을
이 내용을 '원본(남의 리포지토리)'에도 적용시켜줘(PR: Pull Request를 통해 진행)!

## 적용
1. 남의 리포지토리 중 public으로 된 리포지토리를 찾아간다.
2. 그 리포지토리를 들어가면 우상단에 Fork라는 버튼이 있다.
3. Fork는 깃허브 -> 깃허브로 옮겨 오는 것이다.
4. Fork 버튼을 누르면 'Forking 다른 사람 닉네임/다른 사람 리포지토리'가 뜬다.
5. git clone을 통해 fork를 통해 가져온 리포지토리를 내 로컬로 가져온다.
6. 로컬에서 파일을 추가한 후, git add ., git commit, git push를 진행해본다.
7. 그러면, 내 깃허브에는 적용이 되었고, 원본에는 아직 적용이 되지 않았다.
8. PR(pull request)를 통해, 내 것에서 반영된 것을 변경 요청을 하면 된다.
ex>
제목: 깃린이가 파일 추가함
내용: - added gitrini file
9. 원본 리포지토리에 변경 내용을 merge하기 위해서는, 본 계정에서 pr요청을 수락해줘야 한다(Merge pull request).

# 두번째 과제! 저와 협업을 해봅시다. Pull Request
강사님의 리포지토리를 fork하여 PR요청을 보내보자!
## 이 방법은 '오픈 소스'에 기여하는 방법과 같습니다!
이와 같은 방식으로
우리는
- 구글
- 에어비엔비 
등의 코드를 수정할 수 있다.
만약에, 이러한 회사들에 PR을 요청하였는데, 이것이 merge가 되었다?
엄청난 경험이다.

## 구글에 PR요청해보기
위와 동일한 과정으로 구글 계정에 PR을 요청하면 된다.

## 지금까지 배운 명령어 정리
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

* 터미널
HEAD -> main, origin/main
HEAD -> main: 현재 브랜치에서의 커밋 상태를 확인 가능하다.
origin/main: 리모트에 푸시한 커밋 위치를 확인 가능하다.

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

### git remote add origin https://github.com/.... 
라는 명령어를 명령해주면 된다.
git remote add origin (주소)
주소 부분은 Quick setup -- if you've done this kind of thing before
의 HTTPS 부분의 주소를 복사해서 넣어줘도 된다.
3. 리모트에 로컬의 커밋한 내용들을 보내고 싶을 때 사용하는 명령어

### git push origin main
4. commit을 확인해보고 싶으면, commits 부분을 확인하면 된다.

### git clone 레포지토리주소
리모트에 있는 레포지토리 파일들을 복사해서 가져올 수 있다.

### git pull origin main
서버 자체에서 변경이 일어났을 때 가져오는 방법
ex> Add readme

### git reset --hard 커밋해쉬코드(번호)
이전 커밋으로 돌아가는 것도 가능하고,
다시 앞의 커밋으로 되돌리는 것도 가능하다.


