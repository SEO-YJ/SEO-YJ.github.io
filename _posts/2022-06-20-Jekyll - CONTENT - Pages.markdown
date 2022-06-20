---
layout: post
title:  "Jekyll - CONTENT - Pages"
date:   2022-06-20 16:28:00 +0900
categories: Jekyll official documents
---
본 글은 'Git Blog'의 Jekyll 공식문서를 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll에 대해 이해하고, 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!
* Jekyll 버전 4.2.2에 대한 번역입니다.
* 현재 한국어 번역본은 버전 4.0.0입니다. 
* 영어 버전 4.2.2와 한국어 버전 4.0.0을 비교하여 4.2.2 버전에 맞게 번역하여 정리하였습니다!

Jekyll 공식문서 링크: 
    https://jekyllrb.com/docs/

# Pages

Pages are the most basic building block for content. They’re useful for standalone content (content which is not date based or is not a group of content such as staff members or recipes).

Pages는 내용의 가장 기본적인 구성 요소입니다. pages는 단독 내용으로 사용하기에 유용하다 ( 날짜로 구성된 내용이 거나 스태프 멤버들나 레시피와 같이 내용이 그룹화 된 것이 아닌 내용 )

The simplest way of adding a page is to add an HTML file in the root directory with a suitable filename. You can also write a page in Markdown using a .md extension which converts to HTML on build. For a site with a homepage, an about page, and a contact page, here’s what the root directory and associated URLs might look like:

page를 추가하는 가장 간단한 방법은 루트 디렉토리에 적절한 파일이름으로 HTML 파일을 추가하는 것 이다. 또한 마크다운으로 페이지를 작성하여 .md 확장자를 사용하면 빌드 시에 HTML 확장자로 변환된다. 홈페이지, 소개 페이지, 연락처 페이지를 가진 사이트의 경우, 루트 디렉토리의 내용과 관련된 URL들은 다음과 같다:

<!--
.
├── about.md    # => http://example.com/about.html
├── index.html    # => http://example.com/
└── contact.html  # => http://example.com/contact.html 
-->

If you have a lot of pages, you can organize them into subfolders. The same subfolders that are used to group your pages in your project’s source will then exist in the _site folder when your site builds. However, when a page has a different permalink set in the front matter, the subfolder at _site changes accordingly.

만약 많은 페이지들을 가지고 있으면, 하위 폴더로 페이지들을 정리할 수 있다. 프로젝트의 원본에서 페이지들을 그룹화하는데 사용되는 같은 하위폴더들은 사이트 빌드 시에 _site 폴더에 존재할 것 이다. 그러나. 페이지의 front matter에 다른 고유주소가 설정되어 있으면, _site 폴더의 하위 폴더는 이에 맞게 변한다.

<!--
.
├── about.md          # => http://example.com/about.html
├── documentation     # folder containing pages (페이지가 있는 폴더)
│   └── doc1.md       # => http://example.com/documentation/doc1.html
├── design            # folder containing pages (페이지가 있는 폴더)
│   └── draft.md      # => http://example.com/design/draft.html

-->


## Changing the output URL

You might want to have a particular folder structure for your source files that changes for the built site. With permalinks you have full control of the output URL.

빌드된 사이트에 변경한 원본 파일을 위한 특정한 폴더 구조를 원할 수 있다. 고정주소로 출력 URL을 모두 제어할 수 있다.

## Excerpts for pagesPermalink

From Jekyll 4.1.1 onwards, one can choose to generate excerpts for their pages by setting "page_excerpts" to "true" in their config file.

Jekyll 4.1.1 버전 이후로, 설정 파일에 "page_excerpts"를 "true"로 설정하여 페이지에 발췌를 생성할 수 있다.


Why? 
A. 


단어
building: 구성
block: 요소
standalone: 단독
date: 날짜별
simplest: 간단한
permalink: 전자 문서에 고정적으로 부여된 하이퍼링크
accordingly: 따라서, 그에 맞춰
excerpt: 발췌




문법



내 생각
1. page에는 1) 날짜별 내용 2) staff members 3) recipe 와 같은 내용이 들어가면 안된다.
2. page를 추가하는 방법은 1) 확장자 .html 2) 적절한 파일 이름 3) 루트 디렉토리에 저장 
3. page를 마크다운에서 .md 확장자로 저장하면 빌드 시에 .html 확장자로 변환된다.
4. 루트 디렉토리에서 하위 폴더들을 생성하여 그룹화하면 빌드 시에 _site 폴떠에 존재할 것 이다.
5. 페이지에 different parmalink가 설정되면 하위폴더는 변한다.



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
40. config.yml 파일 추가
41. config.yml 파일로 각 게시물들의 front matter에 layout 설정 안 해줘도 됨
42. 작성자들 만의 페이지를 관리하도록 설정
43. Jekyll 플러그인으로 '특정 사용자 정의 내용'을 작성하기 위해 1) Gemfile에 그룹으로 작성 2) _config.yml 파일에 작성
44. bundle update 명령을 수행하면 Jekyll 플러그인이 추가된다. bundle update로 Gemfile에 작성한 것을 추가할 수 있다.
