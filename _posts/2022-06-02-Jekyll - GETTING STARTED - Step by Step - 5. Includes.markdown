---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial - 5. Includes"
date:   2022-06-02 15:31:00 +0900
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

## Includes
The site is coming together; however, there’s no way to navigate between pages. Let’s fix that.

Navigation should be on every page so adding it to your layout is the correct place to do this. Instead of adding it directly to the layout, let’s use this as an opportunity to learn about "includes".

사이트는 그럴싸 해지고 있다; 그러나, 페이지 간에 이동할 방법이 없다. 고쳐보자.

네비게이션은 모든 페이지에서 되야하므로 레이아웃에 추가하는 것이 올바른 방법이다.
레이아웃에 직접적으로 추가하는 것 대신에, 이 기회를 이용해 "includes"에 대해 배워보자.

Why? 그냥 레이아웃에 navigation 추가해서 웹 페이지 간에 이동하면 되는 것 아닌가?
A.


단어


문법
Navigation should be on every page so adding it to your layout is the correct place to do this.
correct place to do this.: 올바른 방법이다.


내 생각
1. includes를 배우면, 웹 페이지 간의 이동(navigation)을 사용할 수 있다. 현재까지, 레이아웃을 이용하여 웹 페이지를 2개(index.html, about.md)를 생성했으므로, 이제, 웹 페이지 간의 이동을 해보자.


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


## Include tag
The "include" tag allows you to include content from another file stored in an "_includes" folder. Includes are useful for having a single source for source code that repeats around the site or for improving the readability.

Navigation source code can get complex, so sometimes it’s nice to move it into an include.

"include" 태그는 당신이 "_includes" 폴더 내에 저장된 다른 파일의 내용을 포함하도록 허용한다. Includes들은 사이트에 반복되는 코드를 단일 소스에서 가지게 하거나, 가독성을 향상시키는데 유용하다.

네비게이션 소스 코드는 복잡한 경우가 많고, 때때로 Include에 이동하는 것이 좋다.


## Include usagePermalink

Create a file for the navigation at <!--_includes/navigation.html--> with the following content:

다음 내용을 따라하여 <!--_includes/navigation.html--> 파일에 네비게이션을 위한 파일을 생성해라.

<!--
<nav>
  <a href="/">Home</a>
  <a href="/about.html">About</a>
</nav>
-->


Try using the include tag to add the navigation to _layouts/default.html:

include tag를 사용하여 _layouts/default.html 파일로의 네비게이션을 추가하는 것을 시도해봐라:


<!--
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {% include navigation.html %}      // include 태그 추가
    {{ content }}
  </body>
</html>
-->

Open http://localhost:4000 in your browser and try switching between the pages.
http://localhost:4000 링크를 브라우저에서 열고 페이지 사이를 이동하는 것을 시도해봐라.


## Current page highlighting

Let’s take this a step further and highlight the current page in the navigation.

<!--_includes/navigation.html--> needs to know the URL of the page it’s inserted into so it can add styling. Jekyll has useful variables available, one of which is "page.url".

Using "page.url" you can check if each link is the current page and color it red if true:

한 단계 더 나아가서 네비게이션에 현재 페이지를 강조해보자.

<!--_includes/navigation.html--> 파일은 include가 삽입된 페이지의 URL을 아는 것이 필요하고 그러면 include는 스타일링을 추가할 수 있다. Jekyll은 유용한 변수들을 사용가능하고, 그 중에 하나가 "page.url"이다.

"page.url" 변수를 사용하여 각 링크가 현재 페이지 인지를 체크할 수 있고, 해당 링크가 참일 경우 그 링크의 색깔을 빨간색으로 칠할 수 있다.

<!--
<nav>
  <a href="/" {% if page.url == "/" %}style="color: red;"{% endif %}>
    Home
  </a>
  <a href="/about.html" {% if page.url == "/about.html" %}style="color: red;"{% endif %}>
    About
  </a>
</nav>
-->

Take a look at http://localhost:4000 and see your red link for the current page.

There’s still a lot of repetition here if you wanted to add a new item to the navigation or change the highlight color. In the next step we’ll address this.

브라우저로 http://localhost:4000 링크를 열고 현재 페이지의 링크가 빨간색인지 확인해라.

네비게이션에 새 아이템(페이지)을 추가하거나 강조 색깔을 변경하기 원하면 여전히 여기에 많은 중복(중복된 코드가 발생)이 있다. 다음 단계에서 이 문제에 대해 다뤄볼 것이다.

Why? 그냥 레이아웃에 navigation 추가해서 웹 페이지 간에 이동하면 되는 것 아닌가?
A. 음,, include 폴더에 네비게이션 소스 코드를 적은 html 파일을 따로 저장해 놓으면, 코드를 분석할 때 쉬울 것 같다.
그냥 네비게이션이 필요한 레이아웃이 적용된 페이지를 위해, 레이아웃에 include 태그만 적어주면 되니까.
Why? include는 왜 페이지의 URL이 필요할까?
A. include파일(<!--_includes/navigation.html-->)을 확인해보니, index.html과 about.md의 주소가 a href 태그에 저장되어있음을 확인할 수 있다. 이를 통해, 이 태그가 둘러싸인 텍스트를 클릭하면 그 해당 URL 페이지로 이동하는 것 같다. 
Why? 많은 페이지를 관리할 때, 페이지를 추가하거나, 색상 변경을 할 경우 중복된 코드가 발생하여 문제가 생긴다는데 왜그럴까?
A. navigation.html 파일의 코드를 확인해보면,
a href="\" if page.url~
로 링크마다 같은 구조의 코드가 작성되는 것을 확인할 수 있다.
이러면 중복아닌가? 중복을 없애주어야 코드를 관리하기 용이하다.

단어
useful: 유용한
repeat: 반복되는
improve: 향상시키다
readability: 가독성
further: 더 나아가
highlight: 강조하다
insert: 삽입하다
color: 칠하다
repetition: 반복
address: 문제


문법
Includes are useful for having a single source for source code that repeats around the site or for improving the readability.
for having~ or for ~ing
동명사 or 동명사 나눠서 해석

Let’s take this a step further and highlight the current page in the navigation.
take this a step further: 한 단계 더 나아가

내 생각
1. includes를 배우면, 웹 페이지 간의 이동(navigation)을 사용할 수 있다. 현재까지, 레이아웃을 이용하여 웹 페이지를 2개(index.html, about.md)를 생성했으므로, 이제, 웹 페이지 간의 이동을 해보자.
2. _include 폴더에 html 파일을 생성 후, Layout에 include 태그를 넣어주면, 
그 레이아웃을 적용한 웹 페이지 간에 이동이 가능하다. 
3. include를 이용해 navigation을 적용하는 방법
1) _include 폴더에 include html 생성
2) html 파일의 내용으로 navigation할 페이지의 URL을 a href 태그로 지정
3) include 파일을 layout 파일에 지정
4) layout을 사용할 페이지를 front matter에 variable로 선언


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
22. 루트 디렉토리에 _includes 폴더를 생성 후, navigation.html 파일을 _includes 폴더 내에 생성하여,
index.html과 about.md 웹 페이지 간의 이동을 가능하게 해보자. 그러기 위해 include 태그를 사용하자.
23. default.html 레이아웃 파일에 include tag를 추가하였다.
24. default.html 레이아웃을 적용한 index.html, about.md 파일에 각각 웹 페이지를 이동하는 링크가 적용되어 서로의 페이지로 이동할 수 있다.

