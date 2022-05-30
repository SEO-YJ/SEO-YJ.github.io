---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial - 2. Liquid"
date:   2022-05-26 14:59:00 +0900
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

## 2. Liquid
Liquid is where Jekyll starts to get more interesting. It is a templating language which has three main components:
* objects
* tags
* filters

Liquid 언어는 Jekyll이 더 흥미를 얻기 시작하는 곳이다. Liquid 언어는 3가지 주요 구성요소들을 가진 템플릿 언어이다.

## Objects
Objects tell Liquid to output predefined variables as content on a page. Use double curly braces for objects: "{{" and "}}".

For example, "{{ page.title }}" displays the page.title variable.

Objects는 Liquid 언어에게 미리 정의된 변수들을 페이지 위의 내용으로써 출력하도록 지시한다. objects를 위해 두개의 중괄호를 사용해라: "{{" and "}}"

예시, "{{ page.title }}"은 "page.title" 변수를 출력한다.

단어
tell: 지시하다
predefine: 미리 정의하다
as: ~로써
curly braces: 중괄호

문법
to 부정사의 부사적 용법

~하도록
Objects(주어) tell(동사) Liquid(목적어) to output(출력 하도록) predefined variables as content on a page.


## Tags
Tags define the logic and control flow for templates. Use curly braces and percent signs for tags: "{%" and "%}".

For example:
<!--
{% if page.show_sidebar %}
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}
-->

This displays the sidebar if the value of the show_sidebar page variable is true.

Learn more about the tags available in Jekyll here.

Tags는 템플릿의 논리 연산과 제어 흐름을 정의한다. tags를 위해 중괄호와 % 문자들을 사용해라: "{%" 와 "%}".

예시:
<!--
{% if page.show_sidebar %} // page.show_sidebar를 보이면,
  <div class="sidebar">    
    sidebar content        // sidebar의 내용
  </div>
{% endif %}                // 보이지 않으면 종료
-->

show_sidebar 페이지 변수의 값이 참이면 sidebar를 출력한다.

Jekyll에서 사용할 수 있는 tags에 대해 더 배우려면 여기를 방문해라.
tags 링크
https://jekyllrb.com/docs/liquid/tags/


## Filters
Filters change the output of a Liquid object. They are used within an output and are separated by a |.

For example:
<!--
{{ "hi" | capitalize }}
-->
This displays Hi instead of hi.

Learn more about the filters available.

Filters는 Liquid object의 출력을 변화시킨다. Filters는 출력 안에서 사용되며 | 로 구분된다.

예시:
<!--
{{ "hi" | capitalize }} // 아마, 필터의 |로 구분하여 대문자(HI)로 출력을 변화시키는 것 같다.
-->

위 코드는 hi 대신에 HI를 출력한다.

사용가능한 filters에 대해 더 배우려면 여기를 참조해라.
filters 링크
https://jekyllrb.com/docs/liquid/filters/

단어
display: 출력하다

## Use Liquid
Now, use Liquid to make your Hello World! text from Setup lowercase:

<!--
...
<h1>{{ "Hello World!" | downcase }}</h1>
...
-->

To make Jekyll process your changes, add front matter to the top of the page:

<!--
---
"# front matter tells Jekyll to process Liquid"
---
-->

Your HTML document should look like this:

<!--
---
---

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
-->

When you reload your browser, you should see hello world!.

Much of Jekyll’s power comes from combining Liquid with other features. Add frontmatter to pages to make Jekyll process the Liquid on those pages.

Next, you’ll learn more about frontmatter.



이제, Setup 파트에서 만든 Hello World글자를 Liquid 언어를 사용하여 소문자로 만들어보자:
<!--
 ...
<h1>{{ "Hello World!" | downcase }}</h1> // 1. {{}}는 objects, 2. | downcase 는 filters
...
-->

당신이 변경한 것을 Jekyll이 처리하게 만드려면, 페이지의 위에 front matter을 추가해라.

<!--
---
"# 머리말은 Jekyll에게 Liquid를 처리하라고 지시한다"
---
-->

당신의 HTML 문서는 이것과 같이 보일 것 이다:

<!--
---
---

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
-->


당신이 브라우저를 다시 로드하면, 당신은 "hello world!"를 볼 것이다.

Jekyll의 힘의 대부분은 Liquid를 다른 기능들과 함께 결합하는 것으로 부터 비롯된다.
머리말을 페이지들에 추가하여 Jekyll이 머리말을 추가한 페이지들에서 Liquid를 처리하도록 만들어라.

다음으로, 당신은 머리말에 대해 배울 것이다.


단어
front matter: 머리말
process: 처리하다
tell: 지시하다
come from: ~로부터 비롯되다
feature: 기능

문법
Add frontmatter to pages to make Jekyll process the Liquid on those pages.
명령문: 해석을 앞에서 부터 하자. 
페이지들에 머리말을 추가해라 ~하도록 해라.

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




