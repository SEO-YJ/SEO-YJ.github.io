---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial - 7. Assets"
date:   2022-06-03 18:21:00 +0900
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

## 7. Assets

Using CSS, JS, images and other assets is straightforward with Jekyll. Place them in your site folder and they’ll copy across to the built site.
CSS, JS, 이미지들과 다른 assets들을 사용하는 것은 Jekyll과 함께라면 간단하다(직관적이다). 그것들을(CSS, JS, images, other assets) 사이트 폴더에 배치하면 그것들은 빌드된 사이트에 복사될 것이다.

Jekyll sites often use this structure to keep assets organized:
Jekyll 사이트들은 assets들을 체계화하는데 이런 구조(아래 구조)를 주로 사용한다:

<!--
.
├── assets
│   ├── css
│   ├── images
│   └── js
...
-->

So, from your assets folder, create folders called css, images and js. Additionally, directly under the root create another folder called ‘_sass’, which you will need shortly.
그래서, assets 폴더에 css, images, js라는 폴더를 생성하라. 추가적으로, 루트 폴더 바로 아래에 '_sass'라는 또 다른 폴더를 생성하라, 이 _sass폴더는 곧 필요할 것이다.


Why?
A.

단어
straightforward: 간단한, 직관적인
organize: 체계화하다, 정리하다
shortly: 곧, 얼마 안되어

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


## Sass
Inlining the styles used in "_includes 폴더의 navigation 파일"(adding or configuring within the same file) is not a best practice. Instead, let’s style the current page by defining our first class in a new css file instead.
"_includes 폴더의 navigation 파일"(같은 파일 내에 추가하거나 구성하는 것) 내에 사용된 인라인 스타일은 가장 좋은 방법은 아니다. 대신에, 새로운 파일 대신에 우리의 첫 번째 class를 정의하여 현재 페이지를 스타일하자.

To do this, refer to the class (that you will configure in the next parts of this step) from within the navigation file by removing the code you added earlier (to color the current link red) and inserting the following code:
이렇게 하려면, 이전에 추가한 코드를 제거하고(현재 링크를 빨간색으로 표기하기 위해) 다음 코드를 삽입하여 "navigation" 파일 내의 클래스(이 단계의 다음 부분에서 구성할 클래스)를 참조하라. 
<!--
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}class="current"{% endif %}>{{ item.name }}</a>
  {% endfor %}
</nav>
-->

You could use a standard CSS file for styling, we’re going to take it a step further by using Sass. Sass is a fantastic extension to CSS baked right into Jekyll.

First create a Sass file at assets/css/styles.scss with the following content:

스타일링을 위해 표준 CSS 파일을 사용할 수 있지만, Sass를 사용하여 한 단계 더 나아갈 것이다.
Sass는 Jekyll에 녹아있는 환상적인 CSS 확장기능입니다. 

다음 내용을 따라 assets/css/styles.scss Sass 파일을 생성하라.
<!--
---
---
@import "main";
-->


The empty front matter at the top tells Jekyll it needs to process the file. The "@import "main"" tells Sass to look for a file called main.scss in the sass directory (_sass/) by default which you already created directly under the root folder of your website).
맨 처음의 빈 front matter은 Jekyll에게 이 파일을 처리해야 한다고 말한다.  "@import "main""은 Sass에게 sass 폴더(웹 사이트의 루트 폴더 바로 아래에 생성한 위치. 기본값: _sass/)에서 main.scss 파일을 참조해야 한다고 말한다.

At this stage you’ll just have a main css file. For larger projects, this is a great way to keep your CSS organized.
이 단계에서 단지 main css 파일만 가지고 있을 것 이다. 더 큰 프로젝트에서는, 이것은 CSS 파일을 정리하는 가장 좋은 방법이다.

Create the current class mentioned above in order to color the current link green. Create a Sass file at "_sass 폴더 내에 main.scss" with the following content:
현재 link를 초록색으로 칠하기 위해서 위에서 언급한 현재 class를 생성하라. 다음 내용을 따라 "_sass 폴더 내에 main.scss"에 Sass 파일을 생성하라.

<!--
.current {
  color: green;
}
-->

You’ll need to reference the stylesheet in your layout.

Open "_layouts 폴더에 default.html 파일" and add the stylesheet to the head 태그:

레이아웃에서 스타일시트를 참조해야 한다.

"_layouts 폴더에 default.html 파일"을 열고 head 태그에 스타일시트를 추가해라:

<!--
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="/assets/css/styles.css">
  </head>
  <body>
    {% include "파일이름" %} // navigation의 html 확장자파일
    {{ content }}
  </body>
</html>
-->

The "styles.css" referenced here is generated by Jekyll from the styles.scss you created earlier in assets/css/.

Load up http://localhost:4000 and check that the active link in the navigation is green.

Next we’re looking at one of Jekyll’s most popular features, blogging.

"styles.css" 파일은 앞서 "assets/css"에 생성한 styles.scss로부터 Jekyll이 생성한 파일이다.

브라우저로 http://localhost:4000 를 열고 네비게이션에서 활동하는 링크가 초록색인지 확인하라.

다음으로 Jekyll의 가장 인기있는 기능 중 하나인, blogging에 대해 배울 것이다.


Why? sass는 Jekyll에 녹아있는 확상적인 css확장 기능이다. 그러면, Jekyll은 Ruby gem인데, sass도 gem일까?
A. .scss 파일을 텍스트 에디터에서 생성하려고 보니 .scss 파일이 생성이 안된다.
확인해보니, sass는 gem으로써 터미널에서 설치해줘야 한다.
그래서, "sudo gem install sass"로 sass를 설치해 주었다.

단어
inline: 인라인의, 그때마다 즉시 처리하는
earlier: 이전에
standard: 표준의
organize: 정리하다
in order to: ~를 위하여
mention: 언급하다
generate: 생성하다


문법
Sass is a fantastic extension to CSS baked right into Jekyll
Sass는 Jekyll에 녹아있는 환상적인 CSS 확장기능입니다. 
1) 뒤의 pp 먼저 해석
2) to: ~의로 해석

내 생각
1. 인라인 스타일링(직접적으로 스타일 코드를 작성)하는 것은 좋은 방식이 아니다.
2. class를 정의하고, sass를 이용하여 스타일링을 하자.
3. sass는 ruby gem이므로 "sudo gem install sass"로 설치해주어야 한다.
4.
<!-- 
---
---            // Jekyll에게 이 파일을 처리해야 한다고 지시. 그러면, Jekyll 정적사이트생성기가 이 파일을 확인하겠지
@import "main"; // _sass 폴더에서 " " 안의 파일을 참조
-->

5. 
<!--
.current {      // current 클래스 생성
 color: green;  // 색상을 초록색으로 칠함
}

-->



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

