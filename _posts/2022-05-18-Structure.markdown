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
|  ├── analytics-providers     # snippets for analytics (Google and custom)
|  |                        
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
