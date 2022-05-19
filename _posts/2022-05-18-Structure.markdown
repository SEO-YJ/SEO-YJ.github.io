---
layout: post
title:  "Structure"
date:   2022-05-18 18:48:00 +0900
categories: Minimal Mistakes A Jekyll theme Guide -> GETTING STARTED
---
본 글은 'Git Blog'의 Jekyll Theme의 가이드라인을 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll Theme를 사용하는 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!

깃 블로그 테마 링크: 
    https://jekyllthemes.io/theme/minimal-mistakes
가이드 링크: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/

# Structure
Nothing clever here. Layouts, data files, and includes are all placed in their default locations. Stylesheets and scripts in assets, and a few development related files in the project’s root directory.
여기 똑똑한 것은 없다. Layouts, data files, includes 파일들은 모두 그들의 기본 위치에 배치된다.
Stylesheets와 assets의 scripts, 그리고 몇몇의 개발파일들은 프로젝트의 루트 디렉토리의 파일들과 관련되어 있다.

내 생각
1. Structure은 구조라는 뜻이다. 
2. 본문에서는 파일들의 '배치'에 관해서 말하는 것 같다.
3. 그러므로, Structure 파트에서는 테마 폴더 파일들의 '배치'가 어떻게 되어있는지 배우는 것 같다.

다음에 정리할 단어
clever: 똑똑한
be placed: 배치되다.


Please note: If you installed Minimal Mistakes via the Ruby Gem method, theme files like _layouts, _includes, _sass, and /assets/ will be missing. This is normal as they are bundled with the minimal-mistakes-jekyll Ruby gem. If you would like to make changes, create the files and Jekyll will prefer your local copy.
please note: 당신이 Ruby Gem method를 통해 Minimal Mistakes를 설치했다면, _layouts, _includes, _sass, 그리고 /assests와 같은 테마 파일들은 누락된다.
그것들은  minimal-mistakes-jekyll Ruby gem과 함계 번들되어 있기 때문에 정상이다.
만약 당신이 파일들을 변경하려는 경우, 파일들을 생성하면 Jekyll은 당신의 로컬 복사본을 선호한다.

내 생각
1. gem 메소드를 통해 Minimal Mistakes를 설치하면 
_layouts, _includes, _sass, 그리고 /assests 와 같은 파일들은 사라진다?
gem으로 테마 파일들을 번들해서 가져오기 때문에?
2. 만약에 내 블로그에 맞게 파일들을 변화하거나 생성하면, 변화하고 생성한 파일이 우선된다는 것 같다.

다음에 정리할 단어
be missing: 누락되다
normal: 정상
change: 변경하다
create: 생성하다
prefer: 선호하다
local copy: 복사본

minimal-mistakes
├── _data                      # data files for customizing the theme
|  ├── navigation.yml          # main navigation links
|  └── ui-text.yml             # text used throughout the theme's UI
├── _includes
|  ├── analytics-providers     # snippets for analytics (Google and custom)
|  ├── comments-providers      # snippets for comments
|  ├── footer
|  |  └── custom.html          # custom snippets to add to site footer
|  ├── head
|  |  └── custom.html          # custom snippets to add to site head
|  ├── feature_row             # feature row helper
|  ├── gallery                 # image gallery helper
|  ├── group-by-array          # group by array helper for archives
|  ├── nav_list                # navigation list helper
|  ├── toc                     # table of contents helper
|  └── ...
├── _layouts
|  ├── archive-taxonomy.html   # tag/category archive for Jekyll Archives plugin
|  ├── archive.html            # archive base
|  ├── categories.html         # archive listing posts grouped by category
|  ├── category.html           # archive listing posts grouped by specific category
|  ├── collection.html         # archive listing documents in a specific collection
|  ├── compress.html           # compresses HTML in pure Liquid
|  ├── default.html            # base for all other layouts
|  ├── home.html               # home page
|  ├── posts.html              # archive listing posts grouped by year
|  ├── search.html             # search page
|  ├── single.html             # single document (post/page/etc)
|  ├── tag.html                # archive listing posts grouped by specific tag
|  ├── tags.html               # archive listing posts grouped by tags
|  └── splash.html             # splash page
├── _sass                      # SCSS partials
├── assets
|  ├── css
|  |  └── main.scss            # main stylesheet, loads SCSS partials from _sass
|  ├── images                  # image assets for posts/pages/collections/etc.
|  ├── js
|  |  ├── plugins              # jQuery plugins
|  |  ├── vendor               # vendor scripts
|  |  ├── _main.js             # plugin settings and other scripts to load after jQuery
|  |  └── main.min.js          # optimized and concatenated script file loaded before </body>
├── _config.yml                # site configuration
├── Gemfile                    # gem file dependencies
├── index.html                 # paginated home page showing recent posts
└── package.json               # NPM build scripts

내 테마 디렉토리와의 비교 및 해석
SEO-YJ.github.io 
(minimal-mistakes host 디렉토리를 포크해서 로컬에 클론해왔기 때문에
내 깃 허브 블로그 리포지토리 이름으로 루트 폴더 생성)
├── _data                      # 테마의 사용자 정의를 위한 데이터 파일들
|  ├── navigation.yml          # 테마의 main 페이지의 네비게이션 링크
|  |                           -> main 페이지 우상단에 "Quick-Start Guide" 배너가 있고,
|  |                           -> 관련 링크가 연결되어 있음을 알 수 있다.
|  |                           -> 이 파일을 이용해, main 페이지에서 다른 사이트와의 
|  |                           -> 네이게이션 역할을 할 수 있다.
|  └── ui-text.yml             # 테마의 UI 전체에서 사용되는 텍스트
|                              -> 여러 나라의 언어들로 정리가 되어있다. 
|                              -> 이름: "기능"으로 되어있다.
|                              -> 아마, 여기서 텍스트를 가져와서 사용하는 거겠지..?
|                              다음에 정리할 단어: throughout: 전체에
|  
├── _includes
|  ├── analytics-providers     # 분석들을 위한 조각들(snippets) (Google and custom)
|  |snippets? : 개발시에 쓰이는 여러 형태의 코드 조각들
|  |https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=ladysov&logNo=50023466991
|  |
|  |                           -> 들어가보니, 무슨 google.html, custom.html
|  |                           -> 이런 파일들 있고, 맥에서 열리지는 않음
|  ├── comments-providers      # 코멘트들을 위한 조각들(snippets)
|  |                           -> 들어가보니, 무슨 custom.html, facebook.html
|  |                           -> 이런 파일들 있고, 맥에서 열리지는 않음
|  ├── footer
|  |  └── custom.html          # 사이트 바닥글에 추가할 사용자 정의 조각들(custom snippets)
|  |                           -> html 파일에 저장된 snippets들을 사용하여
|  |                           -> 쉽게 블로그를 커스텀하는 것 같은데?
|  ├── head
|  |  └── custom.html          # 사이트 헤드에 추가할 사용자 정의 조각들(custom snippets)
|  ├── feature_row             # 특징 행 도우미
|  ├── gallery                 # 이미지 갤러리 도우미
|  ├── group-by-array          # 아카이브에 대한 배열 도우미 그룹
|  ├── nav_list                # 탐색 목록 도우미
|  ├── toc                     # 목차 도우미
|  └── ...
├── _layouts
|  ├── archive-taxonomy.html   # Jekyll 아카이브 플러그인의 태그/카테고리 아카이브
|  ├archive? : 보관 속성, 저장 속성을 가진 파일
|  ├http://mwultong.blogspot.com/2006/09/archive-file-archived-file.html
|  |
|  ├── archive.html            # 보관 기준
|  ├── categories.html         # 카테고리 별로 그룹화 된 게시글 목록 보관
|  ├── category.html           # 특정 카테고리 별로 그룹화 된 게시글 목록 보관
|  ├── collection.html         # 특정 컬렉션 안에 있는 문서 목록 보관
|  ├── compress.html           # HTML 파일 안에 순수 Liquid 언어로 압축
|  |liquid? : Liquid 언어
|  |https://ansohxxn.github.io/blog/liquid/
|  |
|  ├── default.html            # 다른 모든 레이아웃들의 기준
|  ├── home.html               # 홈페이지
|  ├── posts.html              # 연도별로 그룹화된 게시글 목록 보관
|  ├── search.html             # 검색 페이지
|  ├── single.html             # 단일 문서 (post/page/etc)
|  ├── tag.html                # 특정 태그별로 그룹화된 게시글 목록 보관
|  ├── tags.html               # 태그들 별로 그룹화된 게시글 목록 보관
|  └── splash.html             # splash 페이지
|
├── _sass                      # SCSS 부분들
|                              -> .scss 파일들로 구성
|
├── assets
|  ├── css
|  |  └── main.scss            # _sass 폴더로부터 SCSS 부분들이 로드된, main 스타일시트
|  |stylesheet? : HTML 문서에 CSS(SCSS) 스타일을 적용할 때 사용하는 방법
|  ├── images                  # 게시물/페이지/컬렉션/등을 위한 이미지 자료들
|  ├── js
|  |  ├── plugins              # jQuery 플러그인
|  |  ├── vendor               # vendor 스크립트
|  |  ├── _main.js             # jQuery 후에 로드 할 플러그인 세팅과 기타 스크립트
|  |  └── main.min.js          # </body> 전에 로드된 최적화되고 연결된 스크립트 파일
├── _config.yml                # 사이트 구성
├── Gemfile                    # gem 파일 종속성
├── index.html                 # 최근 게시글들을 보여주는 페이지별 홈 페이지
└── package.json               # NPM 빌드 스크립트


