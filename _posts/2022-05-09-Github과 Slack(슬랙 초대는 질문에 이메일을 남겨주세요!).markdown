---
layout: post
title:  "Github과 Slack(슬랙 초대는 질문에 이메일을 남겨주세요!)"
date:   2022-05-09 17:41:00 +0900
categories: Git알못을 위한 깃린이코스(Git, Github 실습위주) 정리
---
# Github와 Slack을 같이 쓰면 개발이 섹시해진다.
## Slack이란?
1. 업무용 메신저
2. 전 세계 50만개 넘는 회사 사용중
3. 글로벌 1위 협업용 메신저
4. 포춘 100대 기업중 65개사가 이용중
5. 많은 프로젝트, 회사에서 협업 도구로 사용된다.
6. 많은 개발도구와 '연동'이된다.

# Slack으로 Github 리포지토리 업데이트 알림 받기
깃허브 리포지토리 구독 방법
1. /github subscribe 깃허브이름/리포지토리이름
2. Add to this conversation

# 세번째 과제! Git린이 코스 슬랙에 본인의 리포지토리를 구독해보세요!
앞으로 프로젝트를 할 때,
1. 슬랙 워크스페이스를 만들고
2. 깃허브 공유 리포지토리를 만들고
3. 슬랙에 구독시키고 협업을 진행하면 된다.

성공!

## 나의 Slack 워크스페이스를 만들어보자!
용도: 내 깃허브의 이벤트를 알림받아 볼 워크스페이스 생성
이름: SwiftWorld
### Slack 무료 평가앱 다운로드
자주 사용하는 이메일을 통해, Slack앱을 맥북에 다운 받는다.

### 앱 추가
Slack 찾아보기 -> 앱 -> Github
여기서 Slack 깃허브 앱을 추가해서 워크스페이스에 저장해놓는다. (무료판은 10개 이하의 앱만 추가 가능하다.)

### 나의 리포지토리 추가
1. /github subscrive SEO-YJ/리포지토리 이름
2. connect Github account
3. Enter code
4. Install Github App
5. Only select repositories -> 리포지토리 선택
6. /github subscrive SEO-YJ/리포지토리 이름 다시 입력



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


