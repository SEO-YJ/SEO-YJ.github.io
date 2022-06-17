---
layout: post
title:  "Jekyll - Build - Rendering Process"
date:   2022-06-17 16:32:00 +0900
categories: Jekyll official documents
---
본 글은 'Git Blog'의 Jekyll 공식문서를 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll에 대해 이해하고, 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!
* Jekyll 버전 4.2.2에 대한 번역입니다.
* 현재 한국어 번역본은 버전 4.0.0입니다. 
* 영어 버전 4.2.2와 한국어 버전 4.0.0을 비교하여 4.2.2 버전에 맞게 번역하여 정리하였습니다!

Jekyll 공식문서 링크: 
    https://jekyllrb.com/docs/

# Rendering Process

참고
rendering
renderer engine.
Render는 html을 입력받아 이 html을 해석해서 모니터로 출력한다. 위 작업을 rendering이라고 한다.


For any Jekyll site, a build session consists of discrete phases in the following order — setting up plugins, reading source files, running generators, rendering templates, and finally writing files to disk.

어느 Jekyll 사이트의 경우, 빌드 세션은 다음 순서에 따른 개별 단계로 구성된다 - 플러그인 세팅, 소스 파일 읽기, 생성기 실행, 템플릿 렌더링, 마지막으로 디스크에 파일 쓰기.

While the phases above are self-explanatory, the one phase that warrants dissection is the rendering phase.

위 단계들은 자명하지만, 해부가 필요한 하나의 단계는 렌더링 단계이다.

The rendering phase is further divisible into three optional stages. Every file rendered, passes through one or more of these stages as determined by the file’s content string, front matter and extension. The stages are akin to an assembly line, with the output from a stage being the input for the succeeding stage:

렌더링 단계는 세 개의 선택적 단계로 더 분할 할 수 있다. 모든 렌더링 된 파일은, 파일의 내용 string, front matter, extention에 결정된 단계들 중 하나 이상을 통과한다. 그 단계들은 assembly 줄과 유사하고, 단계의 출력이 다음 단계의 입력이 된다: 

* Interpreting Liquid expressions in the file
This stage evaluates Liquid expressions in the current file. By default, the interpretation is shallow — in that any Liquid expression in resulting output is not further interpreted. Moreover, any Liquid expression in the file’s front matter is left untouched.

* Liquid 언어를 파일에서 해석하는 것
이 단계는 현재 파일의 Liquid 언어를 평가한다. 기본적으로, 해석은 얕다. - 결과를 출력하는 모든 Liquid 언어는 더 이상 해석되지 않는다. 또한, 파일의 front matter에 있는 모든 Liquid 언어는 그대로 남겨진다.

* Unleashing the converters
This stage invokes the converter mapped to the current file’s extension and converts the input string. This is when Markdown gets converted into HTML and Sass / Scss into CSS or CoffeeScript into JavaScript, etc, etc. Since this stage is determined by the file’s extension, Markdown or Sass inside a ".html" file will remain untouched.

* 변환기 해제
이 단계는 현재 파일의 확장자에 매핑한 변환기를 호출하고 입력 문자열을 변환한다. 이것은 md이 HTML로, Sass / Scss가 CSS로, CoffeeScript가 JavaScript 등으로 변환되는 경우이다. 이 단계는 파일의 확장자에 의해 결정되기 때문에, ".html" 파일 안의 Markdown이나 Sass 그대로 유지된다.

* Populating the layouts
By this stage, the source file is considered rendered and it will not be revisited. However, based on the file’s extension and consequently based on the front matter, it is determined whether to take the output string from the preceding stage and place into layouts or not. Whereas output from Sass files or CoffeeScript files are never placed into a layout, regular text output can go either ways based on whether a layout has been assigned via the front matter.

* 레이아웃 채우기
이 단계에서, 소스 파일은 렌더링이 되었다고 간주되고 다시 검토되지 않는다. 그러나, 파일의 확장자와 결과적으로 front matter을 기준으로 이전 단계의 출력 문자열을 레이아웃으로 가져올지 말지를 결정된다. Sass 파일이나 CoffeeScript 파일들의 출력은 레이아웃에 절대 배치되지 않는 반면에, 일반 텍스트 출력은 레이아웃이 front matter을 통해 할당된지의 여부에 따라서 좌우될 수 있다. 

Placement into layouts work similar to how Russian dolls encase the smaller ones within itself or how an oyster generates a pearl — the converted output from the preceding stage forms the core and layout(s) are successively rendered separately onto the core.

레이아웃 안에 배치하는 것은 러시아 인형이 더 작은 것을 그것 안에 감싸는 방식이나 조개가 진주를 생성하는 방식과 비슷하게 동작한다 - 이전 단계로부터 변환된 출력은 핵심을 형성하고 레이아웃들은 코어에서 개별적으로 연속하게 렌더링된다.


Why? 
A. 


단어
discrete: 별개의, 개별
phase: 단계
self-explanatory: 자명한
warrant: 필요한
dissection: 해부
divisible: 나눌 수 있다, 분할할 수 있다
determine: 결정하다
akin: 유사한
succeeding: 다음의
interpret: 해석하다
moreover: 또한
untouched: 그대로
extension: 확장자
invoke: 호출하다
populating: 채우다
revisit: 재검토하다
precede: 이전의
placement: 배치
form: 형성하다
successively: 연속적으로


문법
with the output from a stage being the input for the succeeding stage
단계의 출력이 다음의 단계의 입력이 된다.



내 생각
1. jekyll의 빌드 과정은 플러그인 세팅, 소스 파일 읽기, 생성기 실행(jekyll), 템플릿 렌더링, 디스크에 파일 쓰기 단계가 일반적이다. 그러나, rendering template 단계는 세부적으로 살펴봐야 한다.
2. 렌더링 단계는 3단계로 나누어 지는데,
1) Liquid 해독
2) 변환기 해제



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
