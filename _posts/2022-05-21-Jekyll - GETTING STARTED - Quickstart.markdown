---
layout: post
title:  "Jekyll - GETTING STARTED - Quickstart"
date:   2022-05-21 17:25:00 +0900
categories: Jekyll official documents
---
본 글은 'Git Blog'의 Jekyll 공식문서를 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll에 대해 이해하고, 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!
* Jekyll 버전 4.2.2에 대한 번역입니다.
* 현재 한국어 번역본은 버전 4.0.0입니다. 
* 영어 버전 4.2.2와 한국어 버전 4.0.0을 비교하여 4.2.2 버전에 맞게 번역하여 정리하였습니다!

Jekyll 공식문서 링크: 
    https://jekyllrb.com/docs/

# Quickstart
Jekyll is a static site generator. It takes text written in your favorite markup language and uses layouts to create a static website. You can tweak the site’s look and feel, URLs, the data displayed on the page, and more.
Jekyll은 정적 사이트 생성기이다. 당신이 좋아하는 마크업 언어로 작성된 텍스트를 Jekyll에 넘겨주면 Jekyll은 이 텍스트를 받고, 레이아웃들을 사용하여 정적인 웹사이트를 생성한다. 사이트의 모양, 느낌, URL들, 페이지 위에 데이터를 표시하는 것 등 여러 동작들을 조정할 수 있다.

내 생각
1. 정적인 웹 사이트란 무엇일까?
정적인 웹 사이트: 컴퓨터 메모장 파일을 보는 것 처럼, 그대로 보이는 사이트
동적인 웹 사이트: 다른 변수들에 의해 변경되어 보이는 사이트

정적 웹 사이트 특징
1. 웹 서버에 '이미 저장되어 있는' html 문서를 고객에게 전송하는 웹 사이트
2. 고객은 서버에 저장되어 있는 html 문서가 변경되지 않는 한 고정된 웹 사이트를 봄
3. 모든 고객은 같은 결과의 웹 페이지를 웹 서버에 요청(request)하고 응답(respond)받음.
ex> 음식메뉴, 포트폴리오 등

동적 웹 사이트 특징
1. 고객이 요청한 정보를 처리한 후에 제작된 html 문서를 고객에게 전송하는 웹 사이트
2. 고객은 상황, 시간, 요청에 따라 다른 웹 사이트를 응답받음
3. 같은 웹 사이트의 페이지라도 다른 페이지를 응답받을 수 있음
4. 고객들이 보는 대부분의 웹 페이지는 동적 웹 사이트
ex> 네이버 블로그, 홈페이지 게시판 등

내가 블로그를 정적 웹사이트로 구성하는 이유
1. 다양한 정보를 조합할 필요가 없다.
2. 고객이 블로그의 내용을 추가, 수정, 삭제할 일이 없다.
3. 저장된 정보만 제공하는 블로그이다.
4. git을 이용하여 웹 사이트를 구성할 수 있다.
5. 마크업 언어를 사용해 볼 수 있다.
6. 개인적인 블로그나, 제출용 포트폴리오는 구축 비용이 적게 드는 정적인 웹 사이트가 적합하다.

정적 vs 동적 웹 사이트 링크
https://blog.naver.com/insaweb/221650456057

2. 정적사이트생성기란 무엇일까?
: 정적인 웹 사이트를 생성해주는 툴

일반적인 정적사이트 생성기
: 마크다운 언어로 작성된 텍스트 -> 미리 html파일을 생성해 고객이 요청하면 html 파일을 응답

정적사이트 생성기 링크
https://iamsang.com/blog/2020/10/10/custom-static-site-generator/

3. Jekyll 웹 사이트 생성 툴은 정적인 웹사이트의 모양, 느낌, URL, 데이터 등을 조정할 수 있다.

단어
take: 넘겨주다
written: 작성된
tweak: 조정하다
displayed: 표시되다

## Prerequisites
Jekyll requires the following:

Ruby version 2.5.0 or higher
RubyGems
GCC and Make
See Requirements for guides and details.

Jekyll 정적 웹 사이트 생성기는 아래 조건들을 요구한다:

1. 루비 버전 2.5.0 이상(ruby -v 로 확인 가능)
2. RubyGems(gem -v 로 확인 가능)
3. GCC and Make(gcc -v 로 확인 가능)
준비물 섹션을 읽어봐라.

내 생각
모든 조건들이 맥북에 갖춰줬다. 이제, Jekyll 정적 웹 사이트 생성기를 사용할 수 있다.

단어
prerequisites: 전제 조건

## Instructions
1. Install all prerequisites.
2. Install the jekyll and bundler gems.

gem install jekyll bundler

3. Create a new Jekyll site at ./myblog.

jekyll new myblog

4. Change into your new directory

cd myblog

5. Build the site and make it available on a local server.

6. Browse to http://localhost:4000


1. Jekyll을 사용한 전제 조건들을 설치한다.

2. Jekyll과 bundler gem을 설치한다.
gem install jekyll bundler

3. ./seo-yj.github.io에 새 Jekyll 사이트를 생성한다.
jekyll new ./

Jekyll 정적 사이트 생성기 툴을 이용해 웹 사이트를 만들고 싶은 폴더로
터미널을 통해 이동한 후, jekyll new ./를 입력하면 된다.

4. 생성된 디렉토리로 이동한다.
우리는 깃허브 리포지토리를 클론하여 로컬로 가져왔으므로,
새로운 폴더가 생성되지는 않고,
클론한 폴더에 Jekyll을 설치해 주었다.

5. 사이트를 빌드하고, 로컬 서버에 적용한다.
루비 gem의 bundle 라이브러리를 이용하여,
bundle exec jekyll serve라는 명령을 통해,
Jekyll을 이용하여 사이트를 빌드하고, 로컬의 서버에서 이를 확인할 수 있다.
로컬 서버주소: http://localhost:4000

6. 브라우저로 http://localhost:4000 에 접속한다.

If you are using Ruby version 3.0.0 or higher, step 5 may fail. You may fix it by adding 'webrick' to your dependencies: bundle add webrick
만약 당신이 ruby 3.0.0 버전 이상을 사용하고 있다면, 5단계에서 아마 실패할 것이다. 당신은 아마 당신의 의존성에 'webrick'를 추가하여 고쳐야 할 것이다 : 'bundle add webrick'

Pass the --livereload option to serve to automatically refresh the page with each change you make to the source files: "bundle exec jekyll serve --livereload"
원본 파일을 변경할 때마다 페이지를 자동으로 새로 고치려면 "--livereload" 옵션을 전달하십시오. "bundle exec jekyll serve --livereload"

If you encounter any errors during this process, check that you have installed all the prerequisites in Requirements. If you still have issues, see Troubleshooting.
만약 이 과정 중에 어떠한 에러를 만난다면, Requirements 파트의 모든 전제 조건들이 설치되었는지 체크해보세요. 만약에 여전히 이슈가 발생한다면, Troubleshooting 파트를 확인하세요.

Installation varies based on your operating system. See our guides for OS-specific instructions.
설치는 OS에 따라 다릅니다. OS별 지침들은 Guides 파트를 확인하세요.

내 과정
0. 깃허브 페이지는 이미 만들어져 있어야 한다.
1) 새로운 repo 생성
2) repo 이름을 username.github.io
3) 로컬에 생성한 repo를 클론
이제 Jekyll 정적 웹 사이트 생성기 툴을 이용하여 블로그를 꾸며보자.

1. Install all prerequisites. (준비 완료)
2. Install the jekyll and bundler gems.

gem install jekyll bundler
로컬에 Jekyll 설치 완료

3. Create a new Jekyll site at ./myblog.

jekyll new myblog

터미널에서 로컬에 클론한 깃 블로그 폴더로 이동하여 jekyll new ./ 입력
후에, bundle install

4. Change into your new directory

cd SEO-Yj.github.io

5. Build the site and make it available on a local server.

bundle exec jekyll serve

Jekyll 정적 웹 사이트 생성기 툴을 로컬 서버에 띄운다.

6. Browse to http://localhost:4000

7. 깃허브 레포지토리에 push

그러면, "seo-yj.github.io"을 브라우저에 요청하면,
 Jekyll 정적 웹 사이트 툴을 이용해 생성한 사이트가 응답함.
 
Github : 웹 서버
Jekyll : 정적 사이트 생성기 툴

깃 허브 페이지 공식문서 링크
https://pages.github.com/

내 생각
1. "bundle exec jekill serve --livereload" 명령을 이용하면,
원본파일이 수정될 때마다 자동으로 페이지를 고쳐주는 명령이다.
그러나, 필자는 글을 완벽히 수정후 git에 commit하여 push 한 내용으로 블로그 글이 수정되길
원하기에 위 명령을 사용하지는 않았다.

단어
vary: 서로 다르다
