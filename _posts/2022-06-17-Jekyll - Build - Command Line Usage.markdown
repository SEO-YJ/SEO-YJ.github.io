---
layout: post
title:  "Jekyll - Build - Command Line Usage"
date:   2022-06-17 14:34:00 +0900
categories: Jekyll official documents
---
본 글은 'Git Blog'의 Jekyll 공식문서를 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll에 대해 이해하고, 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!
* Jekyll 버전 4.2.2에 대한 번역입니다.
* 현재 한국어 번역본은 버전 4.0.0입니다. 
* 영어 버전 4.2.2와 한국어 버전 4.0.0을 비교하여 4.2.2 버전에 맞게 번역하여 정리하였습니다!

Jekyll 공식문서 링크: 
    https://jekyllrb.com/docs/

# Command Line Usage

The "Jekyll" gem makes a jekyll executable available to you in your terminal.

The "jekyll" program has several commands but the structure is always:

<!--
jekyll command [argument] [option] [argument_to_option]

Examples:
    jekyll new site/ --blank
    jekyll serve --config _alternative_config.yml
-->

Why? 
A. 



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
