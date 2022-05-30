---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial - 3. Front Matter"
date:   2022-05-28 16:57:00 +0900
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

## 3. Front Matter
Front matter is a snippet of YAML placed between two triple-dashed lines at the start of a file.

You can use front matter to set variables for the page:

<!--
---
my_number: 5
---
-->

You can call front matter variables in Liquid using the "page" variable. For example, to output the value of the my_number variable above:
<!--
{{ page.my_number }}
-->

Front matter은 파일의 시작 부분에서 두 개의 --- 줄 사이에 배치된 YAML 마크업 언어의 코드조각이다.

Front Matter을 페이지를 위한 변수를 설정하려고 사용할 수 있다.

<!--
---
my_number: 5 // my_number라는 변수를 설정한 것 같다.
---
-->

"page" 변수를 사용하여 Liquid에서 머리말 변수를 호출할 수 있다. (my_number 머리말 변수를 호출 가능)
예를 들어, 위 변수 my_number의 값을 출력하자.

<!--
{{ page.my_number }}
-->


Why? 왜 웹사이트의 페이지에 대한 변수를 선언할까?
A. 페이지의 속성 값을 변경하기 위함이 아닐까?
Why? 페이지의 속성 값을 왜 변경할까?
A. 페이지의 속성 값을 변경하면 페이지의 레이아웃이 변경되지 않을까?
Why? 페이지의 레이아웃을 왜 변경할까?
A. 사이트를 개발자가 원하는 방향으로 구성하여 사용자에게 보여주기 위해서 아닐까? 이게 사용자 인터페이스 관점 아닐까? 그러면, 페이지에 대한 변수를 적절히 선언함으로써 사용자의 사용성을 높여줄 수 있지 않을까?

단어
place: 배치하다
for: ~에 대한, ~를 위한

문법
You can use front matter to set variables for the page:
"당신은 Front Matter을 사용하여 페이지에 대한 변수를 설정할 수 있다."

can ~할 수 있다는 문장 뒤에서 해석
use 사용하여는 문장 앞에서 해석으로
동사를 나눠서 해석할 수 도 있다.

이제 문장 맨 앞에 you를 생략하여 해석하자.


내 생각
1. "2. Liquid 실습 부분"에서 Front Matter을 넣어야 Liquid로 작성된 것이 처리된다고 알 고 있었다.
2. 머리말의 형태는 
1) 파일의 맨 앞에 
2) 
<!--
--- 
"YAML의 코드조각" 
--- 
-->
이다.
3. Front Matter의 변수를 사용하는 방법
1) Front Matter에 변수 선언
<!--
---
my_number: 5
---
-->

2) Liquid에서 사용
여기서는 page에 대한 변수를 사용하였다.
그러면, page에 대한 설정을 해주는 것이겠지?
<!--
{{ page.my_number }}
-->

4. 
아마 이런 프로세스 인 것 같다.
1) my_number: 5 -> my_number에라는 변수에 값 5를 넣어준다.
2) Liquid 언어에 미리 정의된 변수를 사용한다.
여기서는 페이지에 대한 값을 설정하는 page 변수를 사용하였다.
"page.my_number"은 page의 무슨 값을 5로 설정하는 것 같다.
3) 이제 Liquid에서 사용하기 위해,
오브젝트, 태그, 필터 등에서 사용하면 되지 않을까?

5. page 변수는 이미 정의된 변수인 것 같고,
front matter에 변수를 선언하면, page 변수의 하위 변수로 선언되는 것 같다.
그래서, "page.my_number" 형식으로 호출하는 것 같다.

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




## Use front matter
Change the <title> on your site to use front matter:

<!--
---
title: Home
---
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
-->

You must include front matter on the page for Jekyll to process any Liquid tags on it.

To make Jekyll process a page without defining variables in the front matter, use:
<!--
---
---
-->

Next, you’ll learn more about layouts and why your pages use more source code than plain HTML.

front matter을 사용하여 당신의 사이트의 "<title>"을 바꿔봐라:

<!--
---
title: Home // 1. front matter variable로 title 선언, 값은 Home으로 초기화
---
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title> // 2. page 변수를 사용하여, Liquid 내에서 front matter 변수를 호출할 수 있다. page.(front matter variable) 형태로
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
-->

Jekyll이 페이지 위에 있는 어떠한 Liquid tags 든지 처리하려면 front matter을 페이지 위에 반드시 포함해야 한다.

Jekyll이 front matter에 정의한 변수들 없는 페이지를 처리하도록 하려면, 사용해라:
<!--
---
---
-->

다음으로, 더 많은 layouts들과, 왜 당신의 페이지들이 순수 HTML 보다 소스 코드를 더 사용하는 지에 대해 배울 것이다.

단어

문법

내 생각

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




