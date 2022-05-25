---
layout: post
title:  "Jekyll - GETTING STARTED - Ruby 101"
date:   2022-05-23 15:03:00 +0900
categories: Jekyll official documents
---
본 글은 'Git Blog'의 Jekyll 공식문서를 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll에 대해 이해하고, 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!
* Jekyll 버전 4.2.2에 대한 번역입니다.
* 현재 한국어 번역본은 버전 4.0.0입니다. 
* 영어 버전 4.2.2와 한국어 버전 4.0.0을 비교하여 4.2.2 버전에 맞게 번역하여 정리하였습니다!

Jekyll 공식문서 링크: 
    https://jekyllrb.com/docs/

# Ruby 101
Jekyll is written in Ruby. If you’re new to Ruby, this page helps you learn some of the terminology.
Jekyll은 Ruby 언어로 작성되었다. Ruby언어가 처음이라면, 이 페이지는 당신이 몇 가지 Ruby용어를 배울 수 있도록 도울 것 이다.

내 생각
1. Jekyll은 'Ruby gem'이므로 루비 언어로 작성된 툴이다.

단어
terminology: 전문 용어

## Gems
Gems are code you can include in Ruby projects. Gems package specific functionality. You can share gems across multiple projects or with other people. Gems can perform actions like:

* Converting a Ruby object to JSON
* Pagination
* Interacting with APIs such as GitHub

Jekyll is a gem. Many Jekyll plugins are also gems, including jekyll-feed, jekyll-seo-tag and jekyll-archives.

Gem은 루비 프로젝트들에 포함할 수 있는 코드이다. Gem은 특정 기능을 패키지화한다. 당신은 Gem을 통해 패키지화 된 여러 기능들을 여러 프로젝트나 다른 사람들에게 공유할 수 있다. Gem은 아래와 같은 기능들을 수행할 수 있다:

* Ruby 객체를 JSON으로 변환
* 페이지 나누기
* Github와 같은 API와 연동

Jekyll은 gem이다. jekyll-feed, jekyll-seo-tag, jekyll-archives 들을 포함한 많은 Jekyll plugins들도 마찬가지로 gem이다.

내 생각
1. Gem의 기능으로 '깃허브와 같은 API'와의 연동이 가능하다고 한다.
2. 우리는 Jekyll(Ruby gem)을 가지고 Github Page와 연동하여 블로그를 만들었다.
3. Jekyll은 '정적 웹 사이트를 생성하는 기능들이 패키지화된 Ruby gem'이다.
4. 우리는 Jekyll을 만든 개발자가 공유한 Ruby gem을 로컬에 설치하여 사용하고 있다.

단어
package: 패키지화 하다.
functionality: 기능
perform: 수행하다
action: 기능
convert A to B: A를 B로 변환하다.
interact: 연동하다
such as: ~와 같은

## Gemfile
A Gemfile is a list of gems used by your site. Every Jekyll site has a Gemfile in the main folder.

For a simple Jekyll site it might look something like this:

source "https://rubygems.org"

gem "jekyll"

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
end

Gemfile은 당신의 사이트에 사용하는 gem들의 목록이다. 모든 Jekyll 사이트는 메인 폴더 안에 Gemfile을 가지고 있다.

단순한 Jekyll 사이트의 경우 다음과 같이 보일 수 있다.

source "https://rubygems.org"

gem "jekyll"

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
end

내 생각
1. Gemfile은 사용할 gem들의 목록이 담긴 파일이다.
2. 내 Jekyll 폴더에도 Gemfile이 포함되어 있다.
3. Jekyll은 gem이므로, 다른 gem들을 사용할 수 있다.
4. JSON 변환, pagination, API 연동 등의 gem 기능을 사이트에 적용하고 싶으면, Gemfile에 등록해야 할 것 같다.

단어
list: 목록

## Bundler
Bundler is a gem that installs all gems in your Gemfile.

While you don’t have to use Gemfile and bundler, it is highly recommended as it ensures you’re running the same version of Jekyll and its plugins across different environments.

Install Bundler using "gem install bundler". You only need to install it once, not every time you create a new Jekyll project.

To install gems in your Gemfile using Bundler, run the following in the directory that has the Gemfile:

bundle install
bundle exec jekyll serve

To bypass Bundler if you aren’t using a Gemfile, run 

jekyll serve.

See Using Jekyll with Bundler for more information about Bundler in Jekyll and for instructions to get up and running quickly.

Bundler는 당신의 Gemfile 안의 모든 gem들을 설치하는 gem이다. 

당신이 Gemfile과 bundler를 사용하는 것이 필수적이지는 않으나, Gemfile과 bundler를 사용하는 것은 여러 다른 개발환경에서 Jekyll과 Jekyll의 plugins이 올바른 버전을 반드시 실행할 수 있도록 해주기에 적극 권장되고 있다.

"gem install bundler" 명령을 사용하여 Bundler를 설치하라. "gem install bundler" 명령을 통한 로컬에 bundler를 설치하는 것은 당신이 새로운 Jekyll 프로젝트를 생성할 때마다 설치하는 것이 아니라, 한 번만 설치하면 된다. 

Bundler를 사용하여 당신의 Gemfile 안에 있는 모든 gem들을 설치하려면, Gemfile을 가진 폴더 안에서 아래의 명령을 실행해라.(Gemfile을 가진 폴더 안에서 명령을 실행하라는 것은, 터미널의 위치를 Gemfile을 가진 폴더로 이동하여 아래의 명령을 실행하라는 것이다.)

bundle install
bundle exec jekyll serve

bundle install: Gemfile에 등록된 Gem들을 로컬에 설치
bundle exec jekyll serve: 사이트를 빌드
위 명령은 Gemfile에 등록된 버전의 gem들을 사용하도록 보장해준다.
Gemfile을 사용하지 않으면, 그냥 jekyll serve라고 실행하면 된다.

만약 Gemfile을 사용하지 않고 있어서 Bundler를 건너뛰려면, 실행해라
jekyll serve

Jekyll 정적 사이트 생성기 툴의 Bundler gem에 대한 자세한 정보와 빠르게 시작하고 실행하는 명령어들에 대해 알고 싶으면, Using Jekyll with Bundler 튜토리얼을 참조하자.

Using Jekyll with Bundler 링크
https://jekyllrb.com/tutorials/using-jekyll-with-bundler/

내 생각
1. 사이트에 gem의 기능을 사용하려면, Gemfile에 등록만하면 되는 것으로 생각하고 있었는데, Gemfile에 등록한 gem들을 사용하기 위해서는 'bundler'라는 gem을 이용하여 Gemfile에 등록된 gem들을 '설치'해야 한다.
2. Gemfile과 bundler를 사용하는 것이 필수는 아니다. 그러나, 여러 OS에서 동일한 버전의 Jekyll과 플러그인을 실행시켜주기에 사용하자.
3. bundler 역시 gem이다. 따라서, gem 명령어를 이용하여 로컬에 설치하자.
4. gem install bundler를 통해 개발환경에 bundler gem을 설치하면, bundler라는 gem을 이용해, Gemfile의 모든 gem들을 설치할 수 있다. 그러면, "bundle ~"의 명령이 필요하겠지???
5. Gemfile의 모든 gem들을 설치: bundle install
6. 사이트를 빌드: bundle exec jekyll serve
 

단어
don't have to: ~할 필요가 없다
highly: 크게, 매우
recommend: 권장하다, 추천하다
ensure: 반드시 ~하게 하다, 보장하다
run: 실행하다
bypass: 건너뛰다
see: 참조하다
instructions: 명령어
get up: 준비하다

## GETTING STARTED -> Community는 생략
위 파트는 Jekyll을 사용하는 내용이 아닌, 
Jekyll 프로젝트에 기여하거나, 도움을 받고 싶은 경우에 대한 정보이므로 생략하였습니다.

Jekyll 공식문서 GETTING STARTED -> Community 링크
https://jekyllrb.com/docs/community/
