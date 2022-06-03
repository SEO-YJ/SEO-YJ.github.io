---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial - 6. Data Files"
date:   2022-06-03 16:45:00 +0900
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

## 6. Data Files

Jekyll supports loading data from YAML, JSON, and CSV files located in a _data directory. Data files are a great way to separate content from source code to make the site easier to maintain.

In this step you’ll store the contents of the navigation in a data file and then iterate over it in the navigation include.

Jekyll 정적 사이트 생성기는 _data 폴더에 위치한 YAML, JSON, CSV 파일로부터 데이터를 로딩하는 것을 지원한다.
Data files은 소스코드로 부터 내용을 분리하여 사이트를 더 쉽게 유지하게 할 수 있는 좋은 방법이다.

이 단계에서는 데이터 파일에 네비게이션의 내용들을 저장하고 네비게이션 include에서 코드를 반복할 것이다. (반복문을 통해 네비게이션 include를 사용해 볼 것이다.)


## Data file usagePermalink

YAML is a format that’s common in the Ruby ecosystem. You’ll use it to store an array of navigation items each with a name and link.

Create a data file for the navigation at (data폴더 내에 navigation YAML파일) with the following:

<!--
- name: Home
  link: /
- name: About
  link: /about.html
-->

YAML은 Ruby 생태계에서의 흔히 사용되는 형식이다. YAML을 각 이름과 링크로 된 네비게이션 항목들의 리스트를 저장하려고 사용할 것이다.

네비게이션을 위한 데이터 파일을 (data폴더 내에 navigation YAML파일) 에 생성하고 다음을 따르라.


Jekyll makes this data file available to you at "site.data.navigation". Instead of outputting each link in (include폴더 내에 navigation html 파일), now you can iterate over the data file instead:
<!--
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}style="color: red;"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}
</nav>
-->

Jekyll은 "site.data.navigation"로 이 데이터 파일을 사용 가능하게 만들 것 이다. 
include 폴더 내에 navigation html 파일에 각 링크를 출력하는 대신에, 이제 대신에 데이터 파일을 반복문을 사용하여 출력할 수 있다:

The output will be exactly the same. The difference is you’ve made it easier to add new navigation items and change the HTML structure.

What good is a site without CSS, JS and images? Let’s look at how to handle assets in Jekyll.

출력은 완벽하게 동일할 것이다. 차이점은 새로운 네비게이션 항목들을 추가하고 HTML 구조를 변경하는 것을 앞으로 더 쉽게 할 수 있다는 것이다.

CSS, JS, 이미지들 없는 사이트가 뭐가 좋겠냐? Jekyll에서 assets들을 다루는 방법에 대해 알아보자.


Why? 왜 _data 폴더가 있을까?
A. _data 폴더에 data에 관련한 파일들을 YAML, JSON, CSV 등의 형식으로 저장하여 소스코드와 분리시켜 놓으면, 사이트를 관리하는데 편하기 때문이다.
Why? 왜 네이게이션 include를 반복을 통해 사용할까?
A. 앞의 "5. Include" 파트에서 여러 페이지를 추가하거나, 텍스트의 색상을 변경하려면 Liquid코드의 반복이 발생하여 코드를 유지보수하는데 어려움이 생길거라는 문제가 있었다. 그렇기에, data file로 네비게이션의 Liquid코드를 따로 저장하고, 이를 html 파일에서 호출하여 반복문으로 코드를 깔끔하게 작성함으로써 코드의 반복이 생기는 문제를 해결하려는 것 같다.

단어
iterate: 반복(프로그래밍 적으로는 '반복문'이라고 해석)
format: 형식
ecosystem: 생태계
exactly: 완벽하게
handle: 다루다

문법
The difference is you’ve made it easier to add new navigation items and change the HTML structure.
have pp: 과거부터 지금까지 -> 이제 이렇게 만들 수 있다는 것
to add ~ to change: 하나씩 해석


내 생각
1. _data 폴더에는 YAML, JSON, CSV 파일들이 존재하고 Jekyll은 이 파일들의 데이터를 로딩할 수 있다.
2. YAML, JSON, CSV 파일들에 content를 저장해 소스코드와의 분리를 시키면 사이트를 유지 보수하는데 용이하다.
3. 데이터는 YAML, JSON, CSV 파일형식으로 _data 폴더에 저장하여 사이트를 관리하자.
4. 현재 GitBlog 내의 _data 폴더에는 1) navigation 2) text 에 관한 데이터가 YAML 파일 형식으로 저장되어있다.
5. 이 데이터파일이 필요할 경우 html에서 가져다가 사용하나 보다.
6. 반복문을 작성할 때 필요한게 '리스트'인데 리스트를 data폴더에 YAML파일 형식으로 저장해 놓고, 리스트의 요소를 사용하는 방식으로 반복문을 include에서 사용하여 코드를 리팩토링하였다. 이를 통해, 네비게이션의 요소가 많아지더라도, include의 코드는 복잡해지지 않는다.
7. assets에는 JS, CSS, images 등이 있다. images는 데이터가 아닌 assests에 포함되나 보다.

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

