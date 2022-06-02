---
layout: post
title:  "Jekyll - GETTING STARTED - Step by Step Tutorial - 4. Layouts"
date:   2022-05-30 15:35:00 +0900
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

## 4. Layouts
Jekyll supports Markdown in addition to HTML when building pages. Markdown is a great choice for pages with a simple content structure (just paragraphs, headings and images), as it’s less verbose than raw HTML.

Jekyll 정적 사이트 생성기는 페이지들을 만들 때 HTML 뿐만 아니라 Markdown도 지원한다. Markdown은 간단한 내용 구조로 된 페이지들에 좋은 선택이다. (단지 단락들, 표지, 이미지로 구성된 구조일 때), Markdown은 순수 HTML로 구성된 구조보다 간략되어 있다. 

Create a new Markdown file named about.md in your site’s root folder.

사이트의 루트 폴더에 "about.md"라는 이름의 Markdown 파일을 생성해라.

You could copy the contents of index and modify it for the About page. However, this creates duplicate code that has to be customized for each new page you add to your site.

index의 내용(전 실습에서 한 html 파일)들을 복사하고 About 페이지에 맞게 이것을 수정해라. 그러나, 
index의 내용을 복사하여 about 마크다운 파일에 붙여넣기를 하면 당신의 사이트에 추가할 각 새로운 페이지마다 사용자 정의를 해야 하는 중복된 코드를 생성한다.

For example, adding a new stylesheet to your site would involve adding the link to the stylesheet to the "<head>" of each page. For sites with many pages, this is a waste of time.

예를 들어, 사이트에 새로운 스타일시트를 추가하는 것은 스타일시트를 각 페이지의 "<head>" 태그에 연결하는 것을 추가하는 것이 수반된다. 페이지가 많은 사이트의 경우에, 시간 낭비이다.



Why? 왜 Markdown이 HTML보다 간단한 구조의 페이지를 만들 때 좋은 선택일까?
A. 언어가 간략되어 있어서...?
Why? 간략되어 있으면 왜 좋을까?
A. 페이지를 개발자가 더 만들기 쉬워서...? 좀 더 알아보자.
Why? index.html -> about.md로 내용을 복사하면 사이트에서 새로운 페이지를 만들 때마다, '복사 코드'가 생성된다는데 왜 생성될까?
A. 여러 페이지 -> 여러 .md 파일
만약에, 사이트의 모든 페이지의 레이아웃을 변경하고 싶을 경우에 일일히 .md 파일을 열어서 수정해줘야 할까?
오래 걸릴 것 같다. 그러면, 하나만 수정하면 사이트의 모든 페이지의 전체 레이아웃을 변경할 수 있는 방법은 없을까?
그에 대한 문제를 얘기하는 것 같다.

단어
in addition to: ~일 뿐만 아니라
paragraph: 단락
heading: 표지
verbose: 장황한
less verbose: 간략된
raw: 순수
involve: 수반하다


문법

내 생각
1. 마크다운의 장점은 '사이트에 간략한 페이지를 만들 때 유용하다.'
2. 내 Gitblog의 post 폴더 내에 게시글 파일들은 모두 마크다운 언어로 작성된 파일이다.
3. 마크다운의 기능으로는 1) paragraph 2) Heading 3) image 등이 있다.


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





## Creating a layout
Layouts are templates that can be used by any page in your site and wrap around page content. They are stored in a directory called _layouts.
레이아웃은 사이트 내의 모든 페이지에서 사용될 수 있는 템플릿들이고 페이지 내용을 포장한다. 레이아웃은 _layouts라 불리는 폴더 내에 저장된다.

Create the _layouts directory in your site’s root folder and create a new default.html file with the following content:
사이트의 루트 폴더 내에 _layouts 폴더를 생성하고 다음 내용을 따라 dafault.html 파일을 생성해라:

<!--
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {{ content }}
  </body>
</html>
-->

This HTML is almost identical to index.html except there’s no front matter and the content of the page is replaced by a content variable.

content is a special variable that returns the rendered content of the page on which it’s called.

이 default.html 파일은 머리말이 없는 것과 페이지의 content가 content 변수로 배치된 것을 제외하고 거의 동일하다.

"content" 변수는 호출된 페이지의 렌더링된 내용을 반환하는 특별한 변수이다.


Why? 왜 Markdown이 HTML보다 간단한 구조의 페이지를 만들 때 좋은 선택일까?
A. 언어가 간략되어 있어서...?
Why? 간략되어 있으면 왜 좋을까?
A. 페이지를 개발자가 더 만들기 쉬워서...? 좀 더 알아보자.
Why? index.html -> about.md로 내용을 복사하면 사이트에서 새로운 페이지를 만들 때마다, '복사 코드'가 생성된다는데 왜 생성될까?
A. 여러 페이지 -> 여러 .md 파일
만약에, 사이트의 모든 페이지의 레이아웃을 변경하고 싶을 경우에 일일히 .md 파일을 열어서 수정해줘야 할까?
오래 걸릴 것 같다. 그러면, 하나만 수정하면 사이트의 모든 페이지의 전체 레이아웃을 변경할 수 있는 방법은 없을까?
그에 대한 문제를 얘기하는 것 같다.
Layouts은 모든 페이지에서 사용되는 템플릿이며, 페이지의 내용을 포장한다라고 되어있다.
그러면, 스타일시트를 수정할 때, 각 페이지 파일들을 열어서 태그 부분을 수정하는 것이 아니라, _layouts 폴더 내의 Layouts에서 스타일 시트를 1번만 수정을 하면, 모든 페이지의 스타일시트를 수정할 수 있는 것 아닐까? 

단어
identical: 동일한
except: 제외하고는


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


## Use layouts
To make index.html use your new layout, set the "layout" variable in the front matter. The file should look like this:
index.html(전에 만든 파일) 파일에 당신의 새로운 레이아웃(default.html)을 사용하기 위해서, 머리말에 layout 변수를 설정하라. 그 파일은 이것처럼 보여야한다:

<!--
---
layout: default
title: Home
---
<h1>{{ "Hello World!" | downcase }}</h1>
-->


When you reload the site, the output remains the same.

Since the layout wraps around the content on the page, you can call front matter like "page" in the layout file. When you apply the layout to a page, it uses the front matter on that page.

사이트를 다시 로드하면, 출력은 그대로 유지된다.

layout이 페이지의 내용을 포장한 이후로는, front matter을 레이아웃 파일의 "page"처럼 호출 할 수 있다. 레이아웃을 페이지에 적용하면, 그 페이지의 front matter을 사용한다.


Why? 왜 Markdown이 HTML보다 간단한 구조의 페이지를 만들 때 좋은 선택일까?
A. 언어가 간략되어 있어서...?
Why? 간략되어 있으면 왜 좋을까?
A. 페이지를 개발자가 더 만들기 쉬워서...? 좀 더 알아보자.
Why? index.html -> about.md로 내용을 복사하면 사이트에서 새로운 페이지를 만들 때마다, '복사 코드'가 생성된다는데 왜 생성될까?
A. 여러 페이지 -> 여러 .md 파일
만약에, 사이트의 모든 페이지의 레이아웃을 변경하고 싶을 경우에 일일히 .md 파일을 열어서 수정해줘야 할까?
오래 걸릴 것 같다. 그러면, 하나만 수정하면 사이트의 모든 페이지의 전체 레이아웃을 변경할 수 있는 방법은 없을까?
그에 대한 문제를 얘기하는 것 같다.
Layouts은 모든 페이지에서 사용되는 템플릿이며, 페이지의 내용을 포장한다라고 되어있다.
그러면, 스타일시트를 수정할 때, 각 페이지 파일들을 열어서 태그 부분을 수정하는 것이 아니라, _layouts 폴더 내의 Layouts에서 스타일 시트를 1번만 수정을 하면, 모든 페이지의 스타일시트를 수정할 수 있는 것 아닐까? 
Why? 왜 _layout 폴더의 Layouts를 사용하는데, 다른 파일의 front matter에 layout 변수를 선언하여 사용할까?
A. 그게 사용하는 방식인가 보다. 머리말에 layout: default라는 의미는 layout 변수를 선언하고, 값은 기본값을 선언한다는 의미인 것 같다.


단어
identical: 동일한
except: 제외하고는
since: ~때문에
apply: 적용하다


문법
To make index.html use your new layout,
To make: ~하기 위해


내 생각
1. index.html 파일에서 _layouts 폴더의 layouts를 사용하기 위해서는 1) 머리말에 layout 변수 선언


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


## Build the About page
Add the following to about.md to use your new layout in the About page:
About 페이지 안에 새로운 레이아웃을 사용하여 다음 내용을 about.md에 추가해라.

<!--
---
layout: default
title: About
---
# About page

This page tells you a little bit about me.
-->

Open http://localhost:4000/about.html in your browser and view your new page.

Congratulations, you now have a two page website!

Next, you’ll learn about navigating from page to page in your site.

브라우저에서 http://localhost:4000/about.html 이 링크를 누르고 새로운 페이지를 확인해라.
축하한다, 이제 2개의 페이지를 가진 웹사이트가 생겼네!
다음으로, 사이트 내에서 페이지 간의 이동에 대해 배울 것이다.

Why? 왜 Markdown이 HTML보다 간단한 구조의 페이지를 만들 때 좋은 선택일까?
A. 언어가 간략되어 있어서...?
Why? 간략되어 있으면 왜 좋을까?
A. 페이지를 개발자가 더 만들기 쉬워서...? 좀 더 알아보자.
Why? index.html -> about.md로 내용을 복사하면 사이트에서 새로운 페이지를 만들 때마다, '복사 코드'가 생성된다는데 왜 생성될까?
A. 여러 페이지 -> 여러 .md 파일
만약에, 사이트의 모든 페이지의 레이아웃을 변경하고 싶을 경우에 일일히 .md 파일을 열어서 수정해줘야 할까?
오래 걸릴 것 같다. 그러면, 하나만 수정하면 사이트의 모든 페이지의 전체 레이아웃을 변경할 수 있는 방법은 없을까?
그에 대한 문제를 얘기하는 것 같다.
Layouts은 모든 페이지에서 사용되는 템플릿이며, 페이지의 내용을 포장한다라고 되어있다.
그러면, 스타일시트를 수정할 때, 각 페이지 파일들을 열어서 태그 부분을 수정하는 것이 아니라, _layouts 폴더 내의 Layouts에서 스타일 시트를 1번만 수정을 하면, 모든 페이지의 스타일시트를 수정할 수 있는 것 아닐까? 
Why? 왜 _layout 폴더의 Layouts를 사용하는데, 다른 파일의 front matter에 layout 변수를 선언하여 사용할까?
A. 그게 사용하는 방식인가 보다. 머리말에 layout: default라는 의미는 layout 변수를 선언하고, 값은 기본값을 선언한다는 의미인 것 같다. X
현재 우리가 생성한 Layout은 "default.html" 파일이다. 
우리는 Layout을 사용하기 위해서
1) _layouts 폴더를 루트 디렉토리에 생성
2) _layouts 폴더 내에 Layout 파일(html 파일)을 생성
3) _layouts 폴더 내의 Layout을 사용하기 위해서,
루트 디렉토리에 있는 html, md 파일의 front matter에 layout: "Layout 파일명"
이렇게 front matter variable로 선언하면, 해당 페이지에서 layout을 사용할 수 있다.
이렇게 하면, 원하는 layout을 웹 페이지로 가져와서 스타일시트를 수정할 수 있고,
같은 layout을 쓰는 웹 페이지들 끼리는, Layout파일만 수정을 하면,
해당 웹 페이지들의 스타일시트를 한번에 수정할 수 있다.



단어
identical: 동일한
except: 제외하고는
since: ~때문에
apply: 적용하다


문법
To make index.html use your new layout,
To make: ~하기 위해


내 생각
1. index.html 파일에서 _layouts 폴더의 layouts를 사용하기 위해서는 
1) 머리말에 layout: "_layouts 폴더 내의 Layout 중 하나"
2. 지금 _layouts 폴더 내의 레이아웃은 default.html 파일이므로, 
이 파일을 변수로 머리말에 호출하여 사용


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
