---
layout: post
title:  "Structure"
date:   2022-05-20 07:18:00 +0900
categories: Minimal Mistakes A Jekyll theme Guide -> GETTING STARTED
---
본 글은 'Git Blog'의 Jekyll Minimal Mistakes 테마의 가이드라인을 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll Theme를 사용하는 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!

깃 블로그 테마 링크: 
    https://jekyllthemes.io/theme/minimal-mistakes
가이드 링크: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/

# Installation
## Install the theme
1. For a new site, install the minimal-mistakes-jekyll gem, remote theme, or fork the Minimal Mistakes repo on GitHub following the steps outlined in the Quick-Start Guide.

If you plan to host with GitHub Pages be sure to properly setup jekyll-remote-theme as it is required for the theme to work properly.

새로운 사이트의 경우, Quick-Start Guide에 설명된 단계들을 따라서 the minimal-mistakes-jekyll gem과 원격 테마를 설치하거나,  깃허브에 the Minimal Mistakes 리포지토리를 포크한다. 

당신이 Github pages를 호스팅할 계획이면, 테마가 제대로 작동하도록 요구되기 때문에 jekyll-remote-theme를 적절히 설정하여야 합니다.


Jekyll remote theme 링크
https://github.com/benbalter/jekyll-remote-theme

깃허브를 이용한 웹 호스팅 정리
1. 홈페이지에 필요한 것들은 준비했다고 가정(html, css 등)
-> Minimal Mistakes Jekyll theme 깃 리포지토리에서 로컬로 클론했더니, 홈페이지에 필요한 것들은 준비됨
2. 클라이언트 <-> 서버 개념
클라이언트: 고객
서버: 상점

과정 
1) 클라이언트가 서버에 웹 페이지를 요청
2) 서버에서 클라이언트에 웹 페이지를 응답(제공한다.)

클라이언트: 우리가 사용하는 컴퓨터
웹 페이지 요청 방법: 웹 브라우저를 이용해 요청
웹 페이지 응답 방법: 웹 브라우저를 통해, 입력한 '파일'을 서버에서 클라이언트로 제공
서버: 요청하는 '파일'을 가지고 있는 컴퓨터, 24시간 켜져 있어야 한다.(언제 클라이언트에서 웹 페이지를 요청할지 모르니)

잠만,,,,,
지금 필자는 https://seo-yj.github.io/ 라는 웹 페이지를 만들었다.
이는, 웹 브라우저에서 클라이언트가 요청하면 서버에서 파일을 제공해 웹 사이트로 이동할 수 있다.
그러면, 필자는 지금, 온라인 상에서 제공하는 서버를 이용해서 블로그 사이트를 구축한 것 이겠네...?
그러면, 깃 허브에서 제공하는 서버를 이용해서 사이트를 만든 것이겠지??

필자가 깃허브 블로그를 만든 과정
1. 새로운 리포지토리 생성
2. 리포지토리 이름은 seo-yj.github.io 로 생성
3. 내 리포지토리를 로컬로 클론
4. 로컬에 Jekyll 설치
gem install jekyll bundler
5. jekyll 생성
jekyll new ./
6. bundle install
7. Jekyll 로컬 서버에 띄우기
bundle exec jekyll serve
8. remote(내 깃허브 리포지토리)에 push

테마 적용
1. https://github.com/mmistakes/minimal-mistakes 
2. Download ZIP
3. 내 로컬의 github.io 폴더에 다운 파일 복붙
4. bundle install
5. bundle exec jekyll serve
6. remote(내 깃허브 리포지토리)에 push

블로그 설정
1. _config.yml 열기
2. 본인 블로그에 맞게 설정

블로그 만들 때 참조한 링크
https://zeddios.tistory.com/1222
https://zeddios.tistory.com/1223

정리
웹 호스팅이란?
개인이 별도의 서버를 구축하지 않고, 온라인 상의 서버를 이용하여 본인의 웹 페이지를 호스팅하는 것
https://ya-ya.tistory.com/14

2. For an existing site follow the steps outlined in the Quick-Start Guide. Then work through the guidelines below for migration and setup.
기존 사이트의 경우 Quick-Start Guide에 설명된 단계들을 따른다. 그 다음에 "이동과 셋업" 에 대한 아래 지침들을 따르자.

3. For those who’d like to make substantial edits to the theme, download as a ZIP file to customize.
테마에 대한 상당한 편집을 원하면, 사용자정의 할 ZIP 파일을 다운로드하자.

ProTip: Be sure to remove /docs and /test if you forked or downloaded Minimal Mistakes. These folders contain documentation and test pages for the theme and you probably don’t want them littering up in your repo.
ProTip: 당신이 포크했거나 Minimal Mistakes파일을 다운로드 했으며, /docs, /test 폴더를 지워라. 이 폴더들은 테마에 대한 문서와 테스트 페이지들을 포함하고 있고, 당신은 아마 그것들이 당신의 폴더를 어지럽히는 것을 원하지 않을 것이다.
 
Note: The theme uses the jekyll-include-cache plugin which will need to be installed in your Gemfile and added to the plugins array of _config.yml. Otherwise you’ll throw Unknown tag 'include_cached' errors at build.
Note: 테마는 당신의 Gemfile에 설치되는 것을 필요로 하고, _config.yml의 플러그인 배열에 추가되는 것을 필요로 하는 jekyll-include-cache plugin을 사용한다.
    그렇지 않으면, 당신은 빌드 시에 알려지지 않은 태그 'include_cached' 에러들을 발생합니다.
    
## Theme migration
To move over any existing content you’ll want to copy the contents of your _posts folder to the new site. Along with any pages, collections, data files, images, or other assets you may have.
기존 컨텐트를 옮길때, 당신은 당신의 _post 폴더의 컨텐트들을 새로운 사이트에 복사할 것이다. 당신이 가지고 있을 페이지, 컬렉션, 데이터, 이미지 또는 다른 자산들도 마찬가지 일 것이다.

내 생각
1. 기존 블로그의 컨텐츠를 새로운 사이트로 옮기고 싶을 경우에는 _post폴더의 내용을 복사해서 새로운 사이트로 옮겨야 한다.
2. 컨텐츠 뿐만 아니라, 페이지, 컬렉션, 데이터, 이미지 등 다른 asset들도 복사해서 새로운 사이트로 옮긴다.

Next you’ll need to convert posts and pages to use the proper layouts and settings. In most cases you simply need to update _config.yml to your liking and set the correct layout in their YAML Front Matter.
다음으로 당신은 레이아웃과 설정을 적절히 사용하여 게시글과 페이지들을 변경할 것이다. 
대부분의 경우, 당신은 당신의 취향대로 _config.yml 파일을 업데이트 하고, YAML Front Matter에 올바른 레이아웃을 설정한다.

내 생각
1. 레이아웃, 설정들을 이용해 게시글, 페이지들을 설정할 수 있다.
2. 게시글, 페이지들을 취향대로 설정하기 위해, _config.yml, YAML Front Matter을 설정하나 보다.

Front Matter defaults are your friend and I encourage you to leverage them instead of setting a layout and other global options in each post/page’s YAML Front Matter.
Front Matter defaults들은 당신의 친구이고 필자는 각각의 게시글/페이지의 YAML Front Matter에서 레이아웃과 다른 글로벌 옵션들을 설정하는 것 대신에 Front Matter defaults를 활용하기를 권장한다.

내 생각
1. 게시글, 페이지들을 설정하기 위해서, Front Matter defaults를 사용하자.

Posts can be configured to use the single layout — with reading time, comments, social sharing links, and related posts enabled. Adding the following to _config.yml will set these defaults for all posts:
게시글들은 단일 레이아웃을 사용해서 설정될 수 있다 - reading time, comments, social sharing links, 그리고 related posts가 활성화된 상태에서
아래의 내용을 _config.yml 파일에 추가하면 모든 게시글들에 대해 이 기본값들이 설정된다.

내 생각
1. _config.yml 파일의 내용을 변경하면 모든 게시글들의 설정을 변경할 수 있다.

defaults:
   _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      read_time: true
      comments: true
      share: true
      related: true
      
내 생각
1. 내 _config.yml은 위 내용들이 이미 설정되어 있다.

Post/Page Settings: Be sure to read through the “Working with…” documentation to learn about all the options available to you. The theme has been designed to be flexible — with numerous settings for each.
게시글/페이지 설정: 당신이 사용가능한 모든 설정들에 대해 배우려면 "Working with..."라는 문서를 읽어봐라. 테마는 각각 수많은 설정이 있는 유연한 방식으로 설계 되었다.

내 생각
1. 게시글/페이지 설정은 CONTENT -> Working with Posts, Working with Pages, Working with Collections의 문서들을 읽고, 취향대로 설정하자.

## Install dependencies
If this is your first time using Jekyll be sure to read through the official documentation before jumping in. This guide assumes you have Ruby v2 installed and a basic understanding of how Jekyll works.
만약 당신이 Jekyll을 처음 사용한다면 넘어가기전에 "공식 문서"를 반드시 읽어야 한다. 이 가이드에서는 당신이 Ruby 버전 2 이상이 설치되어있고, Jekyll이 작동하는 방식의 기본적인 이해가 있다고 가정한다.

Jekyll 공식 문서
https://jekyllrb.com/docs/

내 생각
1. 지금 필자가 번역하고 이해하고 있는 것은 Jekyll의 'Minimal Mistakes라는 테마'에 대해 공부하고 있는 것
2. 테마에 대해 공부하기 전에, Jekyll에 대한 공부를 먼저해야 한다.
3. 따라서, 우리는 Jekyll 공식 문서를 통해, Jekyll에 대해 공부해보자.
