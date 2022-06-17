---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial - 10. Deployment"
date:   2022-06-15 18:17:00 +0900
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

## 10. Deployment

In this final step we’ll get the site ready for production.
이번 마지막 스텝에서 사이트를 생산할 수 있도록 준비 할 것이다.

## Gemfile

It’s good practice to have a Gemfile for your site. This ensures the version of Jekyll and other gems remains consistent across different environments.

좋은 연습은 당신의 사이트를 위해 Gemfile을 갖는 것이다. Gemfile을 갖는 것은 Jekyll 및 다른 gem들의 버전이 다른 환경에서도 일관되게 유지되게 한다.

Create a 'Gemfile' in the root. The file should be called ‘Gemfile’ and should not have any extension. You can create a Gemfile with Bundler and then add the 'jekyll' gem:

bundle init
bundle add jekyll

루트 폴더에 'Gemfile'을 생성하라. 그 파일은 반드시 'Gemfile'로 이름이 되어 있어야 하고, 어떠한 확장자도 없어야 한다. 
Bundler로 Gemfile을 생성할 수 있고 'jekyll' gem을 추가하라.

파일은 다음과 같아야 한다:

soure "https://rubygems.org"

gem "jekyll"


Bundler installs the gems and creates a "Gemfile.lock" which locks the current gem versions for a future "bundle install". If you ever want to update your gem versions you can run "bundle update".

Bundler는 그 gems들을 설치하고 미래에 "bundle install(bundle 설치)"를 위해 현재 gem 버전들을 잠궈논 Gemfile.lock 파일을 생성한다. 언제든지 gem버전을 업데이트 하고 싶으면 "bundle update"를 명령하라.

When using a "Gemfile", you’ll run commands like "jekyll serve" with "bundle exec" prefixed. So the full command is:
bundle exec jekyll serve

"Gemfile"을 사용하고 있으면, "bundle exec" 명령어가 앞에 고정된 "jekyll serve"같은 명령어들을 실행할 수 있다.
따라서 전체 명령어는:
bundle exec jekyll serve

This restricts your Ruby environment to only use gems set in your "Gemfile".

Gemfile을 사용하고 있는 것은 Ruby 환경이 Gemfile에 설정된 gems만을 사용하도록 제한한다.


## Plugins

Jekyll plugins allow you to create custom generated content specific to your site. There’s many plugins available or you can even write your own.

There are three official plugins which are useful on almost any Jekyll site:

jekyll-sitemap - Creates a sitemap file to help search engines index content
jekyll-feed - Creates an RSS feed for your posts
jekyll-seo-tag - Adds meta tags to help with SEO

Jekyll 플러그인을 사용하면 사이트에 특정한 사용자 정의로 생성된 내용을 생성할 수 있다. 사용 가능한 많은 플러그인이 있고 당신만의 플러그인을 직접 작성할 수도 있다.

거의 대부분의 Jekyll 사이트에서 사용하는 유용한 공식 플러그인이 3개 있다.

jekyll-sitemap - 검색 엔진이 내용을 인덱스하는데 도움을 주는 sitemap 파일을 생성한다.
jekyll-feed - 게시글들을 위한 RSS 피드를 생성한다.
jekyll-seo-tag - SEO에 도움을 주는 메타 태그들을 추가한다.

To use these first you need to add them to your "Gemfile". If you put them in a "jekyll_plugins" group they’ll automatically be required into Jekyll:

이것들을 사용하기 위해 먼저 이것들을 "Gemfile"에 추가해야 한다. "jekyll_plugins" 그룹에 그것들을 넣으면 그들은 자동적으로 Jekyll에 필요될 것 이다.

Then add these lines to your _config.yml:

plugins:
  - jekyll-feed
  - jekyll-sitemap
  - jekyll-seo-tag

_config.yml 파일에 이 줄들을 추가하라:

plugins:
  - jekyll-feed
  - jekyll-sitemap
  - jekyll-seo-tag
  
  Now install them by running a "bundle update".

"jekyll-sitemap" doesn’t need any setup, it will create your sitemap on build.

For "jekyll-feed" and "jekyll-seo-tag" you need to add tags to "_layouts/default.html":

<!--
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="/assets/css/styles.css">
    {% feed_meta %}
    {% seo %}
  </head>
  <body>
    // include 태그로 navigation.html 추가해야 되나 Github push 에러로 해당 라인 제거
    {{ content }}
  </body>
</html>
-->

이제 "bundle update" 명령을 실행하여 그것들을 추가하자.

"Jekyll-sitemap"은 어떠한 설정도 필요 없다, 이것은 빌드시 sitemap을 생성할 것이다.

"jekyll-feed"와 "jekyll-seo-tag"는 "_layouts/default.html" 파일에 태그를 추가해야 한다.

Restart your Jekyll server and check these tags are added to the <head>.

Jekyll 서버를 다시 시작하고 이 태그들이 <head>에 추가되었는지 확인해라.



## Environments

Sometimes you might want to output something in production but not in development. Analytics scripts are the most common example of this.

To do this you can use environments. You can set the environment by using the "JEKYLL_ENV" environment variable when running a command. For example:

Terminal
JEKYLL_ENV=production bundle exec jekyll build


때때로 프로덕션 단계에서는 어떤 것을 출력하길 원하지만 개발단계에서는 출력을 원하지 않은 경우가 있을 것이다. "Anayltics scripts"가 이에 대한 가장 일반적인 예이다.

이것을 하기 위해서 environments를 사용할 수 있다. "Jekyll_ENV" 환경 변수를 사용하여 명령어로 실행시에 environment를 설정할 수 있다.

By default "JEKYLL_ENV" is development. The "JEKYLL_ENV" is available to you in liquid using "jekyll.environment". So to only output the analytics script on production you would do the following:

"JEKYLL_ENV"의 기본값은 development이다. "JEKYLL_ENV"는 "jekyll.environment"를 사용하여 liquid에서 사용가능하게 한다. 프로덕션 시에만 analytics script를 출력하려면 다음을 따라해야 한다:

<!--
{% if jekyll.environment == "production" %}
  <script src="my-analytics-script.js"></script>
{% endif %}
-->

## Deployment

The final step is to get the site onto a production server. The most basic way to do this is to run a production build:

Terminal
JEKYLL_ENV=production bundle exec jekyll build

And then copy the contents of _site to your server.

마지막 단계는 사이트를 프로덕션 서버로 가져오는 것이다. 이것을 하는 가장 기본적인 방법은 프로덕션 빌드를 실행하는 것이다:

Terminal
JEKYLL_ENV=production bundle exec jekyll build

그리고 서버에 _site의 내용을 복사한다.


### Destination folders are cleaned on site builds
The contents of _site are automatically cleaned, by default, when the site is built. Files or folders that are not created by your site's build process will be removed.

Some files could be retained by specifying them within the "keep_files" configuration directive. Other files could be retained by keeping them in your assets directory.

### 사이트 빌드시 목적지 폴더는 깨끗해야 한다.
기본적으로 사이트가 빌드 될 때 _site의 내용들은 자동으로 지워진다. 사이트의 빌드 프로세스에서 생성되지 않은 파일들이나 폴더들은 삭제될 것이다.

일부 파일들은 "keep_files" 구성 지시어 내에서 그들을 지정하여 유지될 수 있다. 다른 파일들은 assets 폴더 내에 그것들을 유지하여 유지될 수 있다.

A better way is to automate this process using a CI or 3rd party.

더 나은 방법은 CI 또는 3rd party를 사용하여 이 과정을 자동화 하는 것이다.

## Wrap up
That brings us to the end of this step-by-step tutorial and the beginning of your Jekyll journey!

Come say hi to the community forums
Help us make Jekyll better by contributing
Keep building Jekyll sites!

이로써 단계별 튜토리얼이 끝나고 Jekyll 여정이 시작될 것이다.



Why? 왜 사이트를 배포할까?
A. 흠,,, 사이트를 브라우저에 배포해야 사람들이 우리의 사이트를 '이용'하지 않을까?
사이트를 만드는 목적이 사람들이 우리 사이트를 이용하게 하려고 하는 것 아닌가.
Why? 어떻게 Jekyll 플러그인으로 '특정한 사용자가 정의한 내용'을 사이트에 생성할 수 있을까?
A. 1) Gemfile과 2)_config.yml에 추가하면 된다.
Why? 왜 analytics scripts를 통해 '프로덕션' 단계에서의 출력만 확인할 까?
A. 테스트하려는 거 아닐까... 아니다.
production이란 실제 서비스를 위한 운영 환경이다.



단어
production: 생산
ensure: 반드시 하게 하다, 보장하다
extension: 확장, 확장자
allow: ~할 수 있다.
first: 먼저
require: 필요하다, 요구하다
most: 가장
common: 일반적인
some: 일부
specify: 지정하다


문법
This ensures the version of Jekyll and other gems remains consistent across different environments.

Gemfile을 갖는 것은 Jekyll 버전을 보장하고 다른 gem들은 지속성을 다른 환경에서도 유지한다.

1. version of ( Jekyll and other gems ) / remains / consistent ( across different environments ).
Jekyll 및 기타 gem의 버전이 / 다양한 환경에서 / 일관되게 유지된다.
2. This ensure ~ : 뒷 문장이 반드시 하게 한다.

내 생각
1. 사이트를 '생산'하기 위해서는 Gemfile이 필요하다.
2. 사이트에 '특정한 사용자 정의 콘텐츠'를 생성하기 위해서는 Jekyll plugin을 사용한다.
3. 플러그인은 1) 가져다 사용하는 플러그인 2) 직접 작성하여 사용하는 플러그인 이 있다.
4. 플러그인을 추가하는 방법은 'Gemfile'의 jekyll_plugins 그룹에 작성하면 된다.
5. 위 플러그인 들로 검색엔진(구글, 네이버 등)에서 잘 검색되게 하는 것 같다.
6. Analytics scripts는 프로덕션 단계에서만 출력을 하게 해준다. 테스트?
7. JEKYLL_ENV 명령어로 environment를 실행할 수 있다.
8. 여기서 말하는 production은 실제 서비스를 위한 운영 환경이다.

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
11. html 페이지에 Liquid 언어를 넣어 텍스트를 편집하여 보았다.
12. 다시, bundle exec jekyll serve로 웹 서버를 실행하였다.
13. html 페이지 수정
  1) front matter 추가
  2) Liquid 내에 page 변수 사용
  3) front matter 변수 사용
14. aboud.md라는 markdown파일 생성
15. 구조를 통일하기 위해 index.html -> about.md 로 복사
16. _layouts 폴더 내에 default.html이라는 Layout 파일 생성
17. index.html 파일의 front matter에 layout 변수를 생성
18. 로컬 웹 서버에서 돌려보니 아직은 index.html 파일의 출력이 이전과 동일
19. about.md 파일의 front matter에 layout: default 변수를 선언해주었다.
20. 로컬 웹 서버를 실행해보니, 이제 2개의 페이지가 생성됬다고 하는데 새로 생긴 페이지를 확인을 못하겠다.
21. 루트 디렉토리의 레이아웃 폴더명을 "layouts" -> "_layouts"로 수정한 후 다시 로컬 웹 서버를 돌렸더니,
http://localhost:4000/about.html 링크에서 about.md 파일의 웹 페이지를 확인할 수 있었다.
22. 루트 디렉토리에 _includes 폴더를 생성 후, navigation 파일을 _includes 폴더 내에 생성하여,
index.html과 about.md 웹 페이지 간의 이동을 가능하게 해보자. 그러기 위해 include 태그를 사용하자.
23. default.html 레이아웃 파일에 include tag를 추가하였다.
24. default.html 레이아웃을 적용한 index.html, about.md 파일에 각각 웹 페이지를 이동하는 링크가 적용되어 서로의 페이지로 이동할 수 있다.
25. include파일(navigation)에 1) 현재 페이지 확인 2) 색상 변경 스타일을 추가하였다.
26. 루트 디렉토리의 data 폴더에 네비게이션을 위한 YAML파일을 생성하고, name과 link로 네비게이션 항목들을 리스트로 저장하였다.
27. 루트 디렉토리에 assets(css, js, images)폴더와 _sass폴더를 생성하였다.
28. include폴더의 navigation 코드 수정(style="color: red;" -> class="current"
29. assets -> css에 style.scss 파일을 생성(main.scss 파일 참조하는 파일 생성)
30. _sass에 main.scss 파일을 생성
31. Jekyll 정적사이트 생성기가 assets에 style.css파일을 생성하였다.
32. _layouts 폴더의 default.html 파일의 head 태그에 link 태그로 css 파일 연결
33. (주의점!: .scss 파일을 vsCode에서 생성할 때, 포맷을 설정하지 말고 파일을 생성한 후에 이름변경에서 .scss 확장자를 추가해주자! 포맷을 설정하여 생성하면, .css, .css.map 파일도 같이 생성되어 에러가 발생한다.)
34. _posts 폴더 생성
35. 2018-08-20-bananas.md 라는 텍스트 게시물 파일 1개 생성
36. _layout 폴더에 post.html 파일로 게시물의 레이아웃 html 파일을 생성
37,. 루트 폴더에 blog.html 파일을 생성하여 게시물들을 리스트로 나열하는 페이지 생성
38. 메인 네비게이션에서 게시물로 이동하기 위해, navigation.yml 파일에 링크를 추가한다.
39. 2개의 게시물 추가
40. config.yml 파일 추가
41. config.yml 파일로 각 게시물들의 front matter에 layout 설정 안 해줘도 됨
42. 작성자들 만의 페이지를 관리하도록 설정
43. Jekyll 플러그인으로 '특정 사용자 정의 내용'을 작성하기 위해 1) Gemfile에 그룹으로 작성 2) _config.yml 파일에 작성
44. bundle update 명령을 수행하면 Jekyll 플러그인이 추가된다. bundle update로 Gemfile에 작성한 것을 추가할 수 있다.
