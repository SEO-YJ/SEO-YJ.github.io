---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial - 9. Collections"
date:   2022-06-10 15:01:00 +0900
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

## 9. Collections

Let’s look at fleshing out authors so each author has their own page with a blurb and the posts they’ve published.

To do this you’ll use collections. Collections are similar to posts except the content doesn’t have to be grouped by date.

각 작성자들이 자신들의 페이지에 광고문구와 그들이 게시한 게시물들을 갖도록 저자들에게 살을 붙이는 것을 찾아보자.

이것을 하려면 collections를 사용한다. Collections는 내용을 날짜별로 그룹화 할 필요가 없는 것을 제외하면 게시물과 유사하다.


## Configuration

To set up a collection you need to tell Jekyll about it. Jekyll configuration happens in a file called "_config.yml" (by default).

Create "_config.yml" in the root with the following:

Collections은 설정하려면 Jekyll에게 컬렉션에 대해 말해야 한다. Jekyll의 collections 설정은 (default로) "_config.yml" 파일에서 발생한다.

"_config.yml" 파일을 다음을 따라 루트 폴더에 생성하라:

<!--
collections:
  authors:
-->
  
To (re)load the configuration, restart the jekyll server. Press "Ctrl+C" in your terminal to stop the server, and then "jekyll serve" to restart it.

(컬렉션)설정을 (재)로드하려면, jekyll 서버를 다시 시작해라. 서버를 멈추기 위해 Ctrl+C 키를 터미널에서 눌러라, 그리고 Jekyll 서버를 재시작하기 위해 "jekyll serve" 명령어를 입력해라.


## Add authors

Documents (the items in a collection) live in a folder in the root of the site named "_*collection_name*". In this case, "_authors"

Create a document for each author:

"_authors/jill.md":

문서들은 (컬렉션의 항목들) "_*collection_name*"이라는 사이트의 루트 폴더 안에 있다. 이 경우에, _authors 폴더이다.

각 작성자에 대한 문서를 만들어보자:

"_authors/jill.md":

_authors/ted.md:


## Staff page

Let’s add a page which lists all the authors on the site. Jekyll makes the collection available at "site.authors".

Create "staff.html" and iterate over "site.authors" to output all the staff:

사이트의 모든 작성자들을 나열하는 페이지를 추가하자. Jekyll은 "site.authors"로 컬렉션을 이용가능하게 만든다.

"staff.html" 파일을 생성하고 모든 스태프들이 출력되도록 site.authors를 반복문에서 사용한다.

<!--
---
layout: default
title: Staff
---
<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2>{{ author.name }}</h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>
-->


Since the content is markdown, you need to run it through the "markdownify" filter. This happens automatically when outputting using "{{ content }}" in a layout.

You also need a way to navigate to this page through the main navigation. Open "_data/navigation.yml" and add an entry for the staff page:

author.content가 마크다운이기 때문에, "markdownify" 필터를 통해 이것을 실행해야 한다. 이것은 레이아웃에서 "{{ content }}" 사용하여 출력할 때 자동적으로 발생한다. 

또한 메인 네비게이션을 통해 이 페이지로 이동할 방법이 필요하다. "_data/navigation.yml" 파일을 열고 스태프 페이지에 항목을 추가하자.


<!--
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
- name: Staff
  link: /staff.html
-->


## Output a page

By default, collections do not output a page for documents. In this case we want each author to have their own page so let’s tweak the collection configuration.

Open "_config.yml" and add "output: true" to the author collection configuration:

기본적으로, collections는 문서 페이지를 출력하지 않는다. 이런 경우에 각 작성자들이 그들만의 페이지를 가지길 원하므로 컬렉션 구성을 수정해보자.

"_config.yml" 파일을 열고 "output: true"를 작성자 collection 구성에 추가하자:

<!--
collections:
  authors:
    output: true
-->

Restart the jekyll server once more for the configuration changes to take effect.

You can link to the output page using "author.url".

Add the link to the "staff.html" page:

<!--
---
layout: default
title: Staff
---
<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2><a href="{{ author.url }}">{{ author.name }}</a></h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>
-->


구성의 변경사항들을 적용하려면 jekyll 서버를 한번 더 재시작해라.

"author.url"을 사용하여 출력 페이지로 연결할 수 있다.

staff.html 페이지로 연결을 추가해라: 
  
  
Just like posts you’ll need to create a layout for authors.

Create "_layouts/author.html" with the following content:

<!--
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}
-->

게시물과 마찬가지로 작성자를 위한 레이아웃을 생성해야 한다.

다음 내용을 따라 "_layouts/author.html"을 생성해라":


## Front matter defaults

Now you need to configure the author documents to use the "author" layout. You could do this in the front matter like we have previously but that’s getting repetitive.

What you really want is all posts to automatically have the post layout, authors to have author and everything else to use the default.

You can achieve this by using front matter defaults in "_config.yml". You set a scope of what the default applies to, then the default front matter you’d like.

Add defaults for layouts to your "_config.yml",

<!--
collections:
  authors:
    output: true

defaults:
  - scope:
      path: ""
      type: "authors"
    values:
      layout: "author"
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
  - scope:
      path: ""
    values:
      layout: "default"
-->

이제 작성자 문서들을 "author" 레이아웃을 사용하여 구성해야 한다. 작성자 문서들을 구성하는 것은 이전에 했던 것 처럼 front matter에서 할 수 있지만 이것은 반복되고 있다.

정말로 원하는 것은 모든 게시물들이 자동적으로 게시물 레이아웃을 가지는 것이고, 작성자들이 작성자를 가지게 하고, 다른 모든 게시물이 기본값을 사용하게 하는 것이다.

_config.yml에서 front matter defaults를 사용하여 달성할 수 있다. 기본값이 적용되는 범위를 설정하고, 원하는 기본 머리말을 설정하라.

_config.yml에 레이아웃에 대한 기본 값을 추가하라,


Now you can remove layout from the front matter of all pages and posts. Note that any time you update _config.yml you’ll need to restart Jekyll for the changes to take effect.

이제 모든 페이지와 게시물들의 front matter에서 레이아웃을 지울 수 있다. _config.yml 파일을 업데이트 할 때마다 Jekyll에 변경사항을 적용하려면 Jekyll을 다시 시작해야 한다.


## List author's posts

Let’s list the posts an author has published on their page. To do this you need to match the author "short_name" to the post "author". You use this to filter the posts by author.

Iterate over this filtered list in "_layouts/author.html" to output the author’s posts:

작성자들이 그들의 페이지들을 게시한 게시물들을 나열하자. 이것을 하려면 작성자 "short_name"을 게시물 작성자와 일치 시켜야한다. 이것을 사용하여 작성자 별로 게시물을 필터링한다.

작성자의 게시물들을 출력하기 위해 필터링 된 리스트를 "_layouts/author.html" 파일에서 반복한다.

<!--
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}

<h2>Posts</h2>
<ul>
  {% assign filtered_posts = site.posts | where: 'author', page.short_name %}
  {% for post in filtered_posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
-->

## Link to authors page

The posts have a reference to the author so let’s link it to the author’s page. You can do this using a similar filtering technique in "_layouts/post.html":

게시물들은 작성자로의 참조를 가지므로 작성자의 페이지로 연결해보자. "_layouts/post.html"에서 유사한 필터링 기술을 사용할 수 있다.

<!--
---
layout: default
---
<h1>{{ page.title }}</h1>

<p>
  {{ page.date | date_to_string }}
  {% assign author = site.authors | where: 'short_name', page.author | first %}
  {% if author %}
    - <a href="{{ author.url }}">{{ author.name }}</a>
  {% endif %}
</p>

{{ content }}
-->

Open up http://localhost:4000 and have a look at the staff page and the author links on posts to check everything is linked together correctly.

In the next and final step of this tutorial, we’ll add polish to the site and get it ready for a production deployment.

브라우저로 "http://localhost:4000"를 열고 스태프 페이지와 작성자 링크를 보고 모든 것이 올바르게 연결되었는지 확인하라.

마지막 단계에서는, 사이트에 세련미를 추가하고, 프로덕션 배포를 위해 준비하자.

Why? 
A. 



단어
flesh out: ~에 살을 붙이다
blurb: 광고 문구, 안내문
set up: 설정하다
item: 항목
live in: ~안에 있다
available: 이용 가능한
entry: 항목
tweak: 조정하다, 수정하다
just like: ~와 마찬가지로
previously: 이전에
repetitive: 반복되는
any time: ~때 마다
match: 일치시키다
filter: 필터링하다
polish: 세련미



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
