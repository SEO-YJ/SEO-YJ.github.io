---
layout: post
title:  "GETTING STARTED"
date:   2022-05-10 16:51:00 +0900
categories: Minimal Mistakes A Jekyll theme Guide
---
본 글은 'Git Blog'의 Jekyll Theme의 가이드라인을 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll Theme를 사용하는 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!

깃 블로그 테마 링크: 
    https://jekyllthemes.io/theme/minimal-mistakes
가이드 링크: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/

# Quick-Start Guide
Minimal Mistakes has been developed as a Gem-based theme for easier use, and 100% compatible with GitHub Pages when used as a remote theme.

If you enjoy this theme, please consider sponsoring me to continue developing and maintaining it.

# 빠른 시작 가이드
Minimal Mistakes는 Gem-based theme를 쉽게 사용하기 위해 이를 기반으로 개발되고 있고, 
원격 테마를 사용할 때 깃 허브와 100% 호환이 된다.

만약 당신이 이 테마를 즐기면, 지속적인 개발과 이것을 유지하기 위해 지원을 고려해주라.

## Instaling the theme
If you’re running Jekyll v3.7+ and self-hosting you can quickly install the theme as a Ruby gem.

ProTip: Be sure to remove /docs and /test if you forked Minimal Mistakes. These folders contain documentation and test pages for the theme and you probably don’t want them littering up your repo.

Note: The theme uses the jekyll-include-cache plugin which will need to be installed in your Gemfile and added to the plugins array of _config.yml. Otherwise you’ll throw Unknown tag 'include_cached' errors at build.

만약에 당신이 Jekyll 3.7 이상의 버전과 self-hosting을 실행하고 있으면, 당신은 Ruby gem으로 테마를 빠르게 설치할 수 있다. 

ProTip: 테마 개발자는 당신이 Mininal Mistakes를 포크했다면, /docs와 /test를 삭제해도
    된다고 확신한다. 이 폴더들은 테마를 위한 문서들과 테스트 페이지들을 포함하며, 당신은 아마도 당신의 리포지토리를 이 문서 파일들이 더럽히는 것을 원하지 않을 것이다.
    
Note: 테마는 당신의 Gemfile에 설치되어야 할 필요가 있고, _config.yml의 플러그인 배열에 추가했을 "jekyll-include-cache 플러그인" 을 사용합니다. 그렇지 않으면, 당신은 
    빌드과정에서 알려지지 않은 태그 'include_cached' 에러들을 만날 것이다.

### Gem-based method
    With Gem-based themes, directories such as the assets, _layouts, _includes, and _sass are stored in the theme’s gem, hidden from your immediate view. This allows for easier installation and updating as you don’t have to manage any of the theme files.
    
    Gem-based 테마들, assets, _layouts, _includes, 그리고 _sass와 같은 폴더들이 당신의 화면에 숨겨져 있는 theme's gem에 저장되어있다.
    Gem-based method는 쉬운 설치를 허락하고, 당신은 여러 테마 파일들의 관리와 같은 업데이트를 할 필요 없다.
    
    To install as a Gem-based theme:
    1. Add the following to your Gemfile :
    
    gem "minimal-mistakes-jekyll"
    
    위 명령어를 터미널에 입력하여 당신의 Gemfile에 따라서 추가해라
    
    2. Fetch and update bundled gems by running the following Bundler command:
    
    bundle
    
    위 명령어를 터미널에 입력하여 Gem 번들들을 패치하고 업데이트 해라
    
    3. Set the theme in your project's Jekyll _config.yml file:
    theme: minimal-mistakes-jekyll
    
    To update the theme run bundle update
    
    위 명령어를 입력하여 당신의 프로젝트의 Jekyll _config.yml 파일을 세팅해라
    
    bundle update 명령어를 입력하여 테마를 업데이트 해라.
    (bundle update를 한 후, git status를 명령해보면 gem이 변화된 것을 확인할 수 있다.)
    
### Remote theme method
    Remote themes are similar to Gem-based themes, but do no require Gemfile changes or whitelisting making them ideal for sites hosted with GitHub Pages.
    원격 테마들은 Gem-based 테마들과 유사하다, 하지만 Gemfile의 변경이나 화이트리스트가 필요하지 않으므로 깃 허브 페이지로 호스팅 되는 사이트에 이상적이다.
    
    To install as a remote theme:
    원격 테마를 설치해보자:
    
    1. Create/replace the contents of your Gemfile with the following:
    아래의 명령어를 따라, 당신의 Gemfile의 내용들을 생성하고/대체해보자.
    (리포지토리를 로컬로 가져오면, 거기에 Gemfile이 들어있다. 거기에 이 텍스트를 넣자.)
    
    source "https://rubygems.org"
    
    gem "github-pages", group: :jekyll_plugins
    gem "jekyll-include-cache", group: :jekyll_plugins
    
    2. Add jekyll-include-cache to the plugins array of your _config.yml
    당신의 _config.yml 리스트의 plugins 파트에 "jekyll-include-cache"를 추가해라.
    (글쓴이는 테마를 이미 가져와서 그런지, 추가되어있었다.)
    
    3. Fetch and update bundled gems by running the following Bundler
    command:
    
    bundle
    
    위 명령어를 터미널에 입력하여 Gem 번들들을 패치하고 업데이트 해라
    
    4. Add remote_theme: "mmistakes/minimal-mistakes@4.24.0" to your 
    _config.yml file. Remove any other theme: or remote_theme: entry.
    당신의 _config.yml 파일에 "mmistakes/minimal-mistakes@4.24.0를 추가해라.
    다른 theme이나 remote_theme은 지워라.
    (글쓴이는 
     "# theme                  : "minimal-mistakes-jekyll"
     "# remote_theme           : "mmistakes/minimal-mistakes"
     이렇게 되어있는 부분을 지우고
     remote_theme             :  mmistakes/minimal-mistakes@4.24.0
     를 추가하였다.)
    
### Remove the Unnecessary

## Setup Your Site
### Starting Fresh
### Starting from jekyll new
### Migrating to Gem Version
### Update Gemfile


# Structure

# Installation

# Upgrading




