---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial - 8. Blogging"
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

## 8. Blogging

You might be wondering how you can have a blog without a database. In true Jekyll style, blogging is powered by text files only.

어떻게 데이터베이스 없이 블로그를 가질 수 있는지 궁금해할 것이다. 진정한 Jekyll 스타일에서, blogging은 오직 텍스트파일만으로 작동된다.

## Posts

Blog posts live in a folder called "_posts". The filename for posts have a special format: the publish date, then a title, followed by an extension.

Create your first post at "_posts/2018-08-20-bananas.md" with the following content:

블로그의 게시물들은 "_posts"라는 폴더에 있다. 게시물들의 파일이름은 특별한 형식을 갖는다: 게시 날짜, 제목, 확장자

다음 내용으로 "_posts/2018-08-20-bananas.md" 라는 첫 게시물을 생성해라.

<!--
---
layout: post
author: jill
---
A banana is an edible fruit – botanically a berry – produced by several kinds
of large herbaceous flowering plants in the genus Musa.

In some countries, bananas used for cooking may be called "plantains",
distinguishing them from dessert bananas. The fruit is variable in size, color,
and firmness, but is usually elongated and curved, with soft flesh rich in
starch covered with a rind, which may be green, yellow, red, purple, or brown
when ripe.
-->

This is like the "about.md" you created before except it has an author and a different layout. "author" is a custom variable, it’s not required and could have been named something like "creator".

이 파일은 작성자(bananas)가 있고 레이아웃이 다른 것을 제외하고 전에 생성한 "about.md"와 비슷하다. "author"은 사용자 정의 변수이며, 이것은 필요하지 않으며(없어도 됨) "생성자"와 같은 이름으로 명명 될 수 있다.


## Layout

The "post" layout doesn’t exist so you’ll need to create it at "_layouts/post.html" with the following content:
"post" 레이아웃은 존재하지 않으므로 다음 내용으로 "_layouts/post.html"에 생성해야 한다

<!--
---
layout: default
---
<h1>{{ page.title }}</h1>
<p>{{ page.date | date_to_string }} - {{ page.author }}</p>

{{ content }}
-->

This is an example of layout inheritance. The post layout outputs the title, date, author and content body which is wrapped by the default layout.

Also note the "date_to_string" filter, this formats a date into a nicer format.

이것은 레이아웃 상속의 예시이다. 게시물 레이아웃은 제목, 날짜, 작성자와 default 레이아웃으로 감싸진 내용의 본문을 출력한다.

또한, "date_to_string" 필터(post layout에 적혀 있다.)를 유의해라, 이 필터는 날짜를 더 좋은 형식으로 포맷한다.


## List posts

There’s currently no way to navigate to the blog post. Typically a blog has a page which lists all the posts, let’s do that next.

Jekyll makes posts available at "site.posts".

Create "blog.html" in your root ("/blog.html") with the following content:

현재 블로그 게시물로 이동할 방법이 없다. 일반적으로 블로그는 모든 게시물들을 나열한 페이지가 있다. 다음을 해보자.

Jekyll은 "site.posts"에 게시물들을 게시한다.

다음 내용을 따라 루트 폴더에 "blog.html" 파일을 생성하라:

<!--
---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2> // 게시물 링크와 제목
      {{ post.excerpt }} // 게시물의 첫 단락
    </li>
  {% endfor %}
</ul>
-->

There’s a few things to note with this code:

* "post.url" is automatically set by Jekyll to the output path of the post
* "post.title" is pulled from the post filename and can be overridden by setting title in front matter
* "post.excerpt" is the first paragraph of content by default

이 코드에는 유의할 몇 가지 사항이 있다:

* "post.url"은 Jekyll에 의해 게시물의 출력 경로에 자동으로 설정된다.
* "post.title"은 게시물의 파일 이름을 가져오고 앞에 있는 제목을 설정하여 제목을 재정의할 수 있다.
* "post.excerpt"는 기본적으로 내용의 첫 번째 단락이다.


You also need a way to navigate to this page through the main navigation. Open "_data/navigation.yml" and add an entry for the blog page:

메인 네비게이션을 통해 이 페이지로 이동할 방법이 필요하다. "_data/navigation.yml" 파일을 열고 블로그 페이지에 대한 항목을 추가한다.

<!--
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
-->



## More posts

A blog isn’t very exciting with a single post. Add a few more:

블로그는 1개의 게시물로 흥미롭지 않다. 몇 가지를 더 추가하자: 

_posts/2018-08-21-apples.md:
<!--
---
layout: post
author: jill
---
An apple is a sweet, edible fruit produced by an apple tree.

Apple trees are cultivated worldwide, and are the most widely grown species in
the genus Malus. The tree originated in Central Asia, where its wild ancestor,
Malus sieversii, is still found today. Apples have been grown for thousands of
years in Asia and Europe, and were brought to North America by European
colonists.
-->

_posts/2018-08-22-kiwifruit.md:

<!--
---
layout: post
author: ted
---
Kiwifruit (often abbreviated as kiwi), or Chinese gooseberry is the edible
berry of several species of woody vines in the genus Actinidia.

The most common cultivar group of kiwifruit is oval, about the size of a large
hen's egg (5–8 cm (2.0–3.1 in) in length and 4.5–5.5 cm (1.8–2.2 in) in
diameter). It has a fibrous, dull greenish-brown skin and bright green or
golden flesh with rows of tiny, black, edible seeds. The fruit has a soft
texture, with a sweet and unique flavor.
-->

Open http://localhost:4000 and have a look through your blog posts.

Next we’ll focus on creating a page for each post author.

브라우저로 http://localhost:4000 링크를 열고 블로그 게시물들을 훑어보세요.

다음으로 각 게시물 작성자를 위한 페이지를 만드는 것에 집중할 것이다.



Why? 
A. 

단어
In true: 진정한
power: 작동하다
post: 게시물
publish: 게시하다
author: 작성자
name: 명명하다
body: 본문
note: 유의하다
currently: 현재
make post: 게시물을 게시하다.
paragraph: 단락
entry: 항목




문법
You might be wondering how you can have a blog without a database.
might be ~ing: ~하는 중 일 것이다.


내 생각
1. Jekyll은 오직 텍스트파일만을 게시물로 사용하고, 데이터베이스가 없다.
2. 게시물 파일의 이름은 게시날짜, 제목, 확장자 등의 형식으로 작성해야 한다.
3. 2018-08-20-bananas.md 라는 텍스트 게시물 파일에서 layout: post를 사용하는데, _layouts에 post layout이 없으므로, 생성해주어야 한다.


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
