---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial"
date:   2022-05-25 14:59:00 +0900
categories: Jekyll official documents
---
본 글은 'Git Blog'의 Jekyll 공식문서를 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll에 대해 이해하고, 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!
* Jekyll 버전 4.2.2에 대한 번역입니다.
* 현재 한국어 번역본은 버전 4.0.0입니다. 
* 영어 버전 4.2.2와 한국어 버전 4.0.0을 비교하여 4.2.2 버전에 맞게 번역하여 정리하였습니다!

Jekyll 공식문서 링크: 
    https://jekyllrb.com/docs/

# Step by Step Tutorial

## 1. Setup
Welcome to Jekyll’s step-by-step tutorial. This tutorial takes you from having some front-end web development experience to building your first Jekyll site from scratch without relying on the default gem-based theme.

Jekyll의 단계별 튜토리얼에 오신 것을 환영한다. 이 튜토리얼은 "default gem-based theme"에 의존하지 않고, 
당신의 첫 Jekyll 사이트를 구축하여 약간의 프론트엔드 웹 개발을 경험할 수 있다.


내 생각
1. 이 튜토리얼을 따라하면, 1) Jekyll 사이트를 구축할 수 있고, 2) 프론트엔드 웹 개발 경헝을 해볼 수 있다.

단어
rely on: 의존하다


## Installation
Jekyll is a Ruby gem. First, install Ruby on your machine. Go to Installation and follow the instructions for your operating system.

With Ruby installed, install Jekyll from the terminal:

gem install jekyll bundler

Create a new "Gemfile" to list your project’s dependencies:

bundle init

Edit the "Gemfile" in a text editor and add jekyll as a dependency:

gem "jekyll"

Run "bundle" to install jekyll for your project.

You can now prefix all jekyll commands listed in this tutorial with "bundle exec" to make sure you use the jekyll version defined in your "Gemfile".




Jekyll은 Ruby gem이다. 첫번째로, 당신의 컴퓨터에 Ruby를 설치하라. "Installation"파트로 가서 당신의 운영체제에 맞는 지시들을 따라해라.

Ruby가 설치되었으면, 터미널로 부터 아래 명령을 입력하여 Jekyll을 설치해라:

gem install jekyll bundler

당신의 프로젝트의 의존요소들의 목록인 새로운 "Gemfile"을 아래 명령을 입력하여 설치해라:

bundle init

텍스트 편집기에서 Gemfile을 편집하고 jekyll을 의존성으로 추가해라:

gem "jekyll"

당신의 프로젝트에 jekyll을 설치할 "bundle" 명령을 실행하라.

당신은 이제 "bundle exec" 명령을 이 튜토리얼에 나열된 모든 jekyll 명령어들 앞에 붙일 수 있고, "bundle exec" 명령을 붙여 실행하면 당신의 Gemfile 안에 정의된 버전의 jekyll을 사용할 수 있다.

내 프로젝트 과정
1. jekyll gem, bundler gem은 이미 로컬에 설치가 되어 있으므로 생략
2. bundler gem은 이미 설치가 되어있으므로, bundle ~ 명령어는 사용 가능
3. bundle init 명령을 통해, 프로젝트에 Gemfile 생성
4. Gemfile 텍스트 편집기에서 gem "jekyll"을 등록하여 Gemfile 의존요소에 jekyll gem을 추가
5. bundle 명령을 통해, 프로젝트에 jekyll 설치
6. 터미널 명령에서 "bundle exec"을 앞에 붙이면, Gemfile 안에 정의된 버전에 따른 gem들을 사용할 수 있다.

단어
dependency: 의존성
listed: 나열된
make sure: 확실하게 하다, 반드시 ~하게 하다


## Create a site
It’s time to create a site! Create a new directory for your site and name it whatever you want. Through the rest of this tutorial we’ll refer to this directory as root.

You can also initialize a Git repository here.

One of the great things about Jekyll is there’s no database. All content and site structure are files that a Git repository can version. Using a repository is optional but is recommended. You can learn more about using Git by reading the Git Handbook.

Let’s add your first file. Create index.html in root with the following content:

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>

사이트를 생성할 시간이다! 당신의 사이트를 위한 새로운 폴더를 생성하고 당신이 원하는 대로 이름지어라.
남은 튜토리얼에서 우리는 이 폴더를 "root"로 참조할 것 이다.

당신은 또한 이 폴더를 Git repository로 초기 설정할 수 있다.

Jekyll의 장점 중 하나는 데이터 베이스가 없다는 것이다. 모든 컨텐츠와 사이트의 구조는 Git 리포지토리가 버전관리 할 수 있는 파일이다. 리포지토리를 사용하는 것은 선택 사항이지만 권장된다. 당신이 Git을 사용하는 것에 대해 더 배우고 싶으면 Git Handbook을 참조해라.

Git Handbook 링크
https://docs.github.com/en/get-started/using-git/about-git

당신의 첫번째 파일을 추가하자. 루트 폴더에 다음 내용을 따라서 index.html 파일을 생성하자.

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>

내 프로젝트 과정
1. jekyll gem, bundler gem은 이미 로컬에 설치가 되어 있으므로 생략
2. bundler gem은 이미 설치가 되어있으므로, bundle ~ 명령어는 사용 가능
3. bundle init 명령을 통해, 프로젝트에 Gemfile 생성
4. Gemfile 텍스트 편집기에서 gem "jekyll"을 등록하여 Gemfile 의존요소에 jekyll gem을 추가
5. bundle 명령을 통해, 프로젝트에 jekyll 설치
6. 터미널 명령에서 "bundle exec"을 앞에 붙이면, Gemfile 안에 정의된 버전에 따른 gem들을 사용할 수 있다.
7. 사이트를 위한 폴더 생성? 근데, 폴더를 생성하고 이미 bundle init을 통해 Gemfile을 생성하였는데, 또 폴더를 생성한다고? 필자는 일단 Gemfile을 생성한 폴더를 root폴더로 생각하고 진행.
    (Git blog minimal-mistakes theme 폴더 형식을 따름)
8. 깃을 이용하여 버전관리 할 수 있다고 하므로 해보자.
9. html 파일 생성 후 저장



단어
root: 참조하다
initialize: 초기화하다, 초기 설정하다
optional: 선택 사항


## Build
Since Jekyll is a static site generator, it has to build the site before we can view it. Run either of the following commands to build your site:

jekyll build - Builds the site and outputs a static site to a directory called _site.
jekyll serve - Does jekyll build and runs it on a local web server at http://localhost:4000, rebuilding the site any time you make a change.

When you’re developing a site, use jekyll serve. To force the browser to refresh with every change, use jekyll serve --livereload. If there’s a conflict or you’d like Jekyll to serve your development site at a different URL, use the --host and --port arguments, as described in the serve command options.

Jekyll은 정적 사이트 생성기로써, 우리가 사이트를 보려면 먼저 Jekyll로 사이트를 빌드해야 한다. 당신의 사이트를 빌드할 다음 명령어 중 하나를 실행하라.

"jekyll build" - 사이트를 빌드하고 _site라는 폴더에 정적 사이트를 생성한다.
"jekyll serve" - "jekyll build" 명령어와 동일한 명령을 수행하고, 추가적으로 "http://localhost:4000" 로컬 웹 서버를 실행하고, 당신이 사이트의 내용을 변경하면 사이트를 재빌드 한다.

당신이 사이트를 개발 중이라면, "jekyll serve" 명령을 사용해라. 매번 변경될 때마다 브라우저(사이트)를 가장 최신 정보로 리프레시 하길 강요하려면, "jekyll serve --liverload" 명령어를 사용해라. 충돌이 있거나 당신은 Jekyll이 당신의 개발 사이트를 다른 URL에서 서비스하기를 바란다면, "serve command options"에 설명되어진 대로, --host나 --port 인자 명령어들을 사용해라, .
serve command options 링크
https://jekyllrb.com/docs/configuration/options/#serve-command-options

The version of the site that jekyll serve builds in _site is not suited for deployment. Links and asset URLs in sites created with jekyll serve will use https://localhost:4000 or the value set with command-line configuration, instead of the values set in your site’s configuration file. To learn about how to build your site when it’s ready for deployment, read the Deployment section of this tutorial.
_site 폴더를 "jekyll serve" 명령어로 빌드하는 사이트의 버전은 배포에 적합하지 않다. "jekyll serve" 명령어로 생성된 사이트 안의 Links와 URLs는 당신의 사이트의 구성 파일에 설정된 값 대신에, https://localhost:4000 나 명령줄 구성으로 설정된 값을 사용할 것이다. 배포할 준비가 되었을 때 당신의 사이트를 빌드할 방법에 대해 배우려면, 이 튜토리얼의 "Deployment section"을 참조해라.

Run jekyll serve and go to http://localhost:4000 in your browser. You should see “Hello World!”.

At this point, you might be thinking, “So what?”. The only thing that happened was that Jekyll copied an HTML file from one place to another.

Patience, young grasshopper, there’s still much to learn!

Next. you’ll learn about Liquid and templating.

"jekyll serve" 명령을 실행하고 당신의 브라우저에서 http://localhost:4000 로 접속하여라. 당신은 "Hello World!"를 볼 것이다. 
이 시점에서, 당신은 아마 생각하고 있을 지도 모른다, "그래서?". 유일하게 발생한 일은 Jekyll이 HTML파일을 한 곳에서 다른 곳으로 복사한 것이다.

참아라. 어린 베짱이여, 여전히 배울게 많다!

다음으로. 당신은 Liquid언어와 templating에 대해 배울 것이다.


내 프로젝트 과정
1. jekyll gem, bundler gem은 이미 로컬에 설치가 되어 있으므로 생략
2. bundler gem은 이미 설치가 되어있으므로, bundle ~ 명령어는 사용 가능
3. bundle init 명령을 통해, 프로젝트에 Gemfile 생성
4. Gemfile 텍스트 편집기에서 gem "jekyll"을 등록하여 Gemfile 의존요소에 jekyll gem을 추가
5. bundle 명령을 통해, 프로젝트에 jekyll 설치
6. 터미널 명령에서 "bundle exec"을 앞에 붙이면, Gemfile 안에 정의된 버전에 따른 gem들을 사용할 수 있다.
7. 사이트를 위한 폴더 생성? 근데, 폴더를 생성하고 이미 bundle init을 통해 Gemfile을 생성하였는데, 또 폴더를 생성한다고? 필자는 일단 Gemfile을 생성한 폴더를 root폴더로 생각하고 진행.
    (Git blog minimal-mistakes theme 폴더 형식을 따름)
8. 깃을 이용하여 버전관리 할 수 있다고 하므로 해보자.
9. html 파일 생성 후 저장
10. jekyll serve 명령으로 사이트 생성 및 웹 서버를 실행 및 내용 변경 시 재빌드

단어
have to: ~해야 한다
since: ~로써
either: ~ 중에 하나
output: 생성하다
run: 구동하다
force: ~강요하다, ~을 하도록 하다
refresh: (가장 최신 정보로)리프레시 하다
every: 매번
would like: ~하고 싶다.
deployment: 배포
should: ~일 것이다.
at this point: 이 시점에서

문법
To force the browser to refresh with every change,
문장 전체: to부정사의 부사적 용법 -> ~하도록

to refresh: to부정사의 형용사적 용법 -> ~할
매 변경마다 브라우저를 새로운 정보로 리프레시 하길 강요하려면,

There's a confilct
존재문
충돌이 있다.

The version of the site: 무생물의 소유격 -> 앞, 뒤 위치가 바뀐다.
사이트의 버전

,instead of
~대신에 로 주어 다음에 ,뒤의 문장을 해석하고 다음 문장 구성을 해석하자.


would like 명사 to 동사원형 목적어: 명사가 목적어를 동사원형하도록 하고 싶다.
ex> I'd like you to drink some coffee: 나는 당신이 커피를 좀 마시기를 바란다.

