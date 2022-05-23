---
layout: post
title:  "Quick-Start Guide"
date:   2022-05-10 16:51:00 +0900
categories: Minimal Mistakes A Jekyll theme Guide -> GETTING STARTED
---
본 글은 'Git Blog'의 Jekyll Minimal Mistakes 테마의 가이드라인을 해석하고 적용해는 것이 목적입니다.
이 글을 통해, Jekyll Theme를 사용하는 깃 블로그 유저분들이 본인만의 블로그를 꾸며 나가는데 도움이 되길 바랍니다!

깃 블로그 테마 링크: 
    https://jekyllthemes.io/theme/minimal-mistakes
가이드 링크: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/

# Quick-Start Guide
Minimal Mistakes has been developed as a Gem-based theme for easier use, and 100% compatible with GitHub Pages when used as a remote theme.

If you enjoy this theme, please consider sponsoring me to continue developing and maintaining it.

Minimal Mistakes는 Gem-based theme를 쉽게 사용하기 위해 이를 기반으로 개발되고 있고, 
원격 테마를 사용할 때 깃 허브와 100% 호환이 된다.

만약 당신이 이 테마를 즐기면, 지속적인 개발과 이것을 유지하기 위해 지원을 고려해주라.

## Instaling the theme
If you’re running Jekyll v3.7+ and self-hosting you can quickly install the theme as a Ruby gem.

ProTip: Be sure to remove /docs and /test if you forked Minimal Mistakes. These folders contain documentation and test pages for the theme and you probably don’t want them littering up your repo.

Note: The theme uses the jekyll-include-cache plugin which will need to be installed in your Gemfile and added to the plugins array of _config.yml. Otherwise you’ll throw Unknown tag 'include_cached' errors at build.

만약에 당신이 Jekyll 3.7 이상의 버전과 self-hosting을 실행하고 있으면, 당신은 Ruby gem으로 테마를 빠르게 설치할 수 있다. 

ProTip: 테마 개발자는 당신이 Mininal Mistakes를 포크했다면, /docs와 /test를 삭제해도
    된다고 확신한다. 이 폴더들은 테마를 위한 문서들과 테스트 페이지들을 포함하며, 당신은 아마도 당신의 리포지토리를 이 문서 파일들이 더럽히는 것을 원하지 않을 것이다.
    
Note: 테마는 당신의 Gemfile에 설치되어야 할 필요가 있고, _config.yml의 플러그인 배열에 추가했을 "jekyll-include-cache 플러그인" 을 사용합니다. 그렇지 않으면, 당신은 
    빌드과정에서 알려지지 않은 태그 'include_cached' 에러들을 만날 것이다.

### Gem-based method
    With Gem-based themes, directories such as the assets, _layouts, _includes, and _sass are stored in the theme’s gem, hidden from your immediate view. This allows for easier installation and updating as you don’t have to manage any of the theme files.
    
    Gem-based 테마들, assets, _layouts, _includes, 그리고 _sass와 같은 폴더들이 당신의 화면에 숨겨져 있는 theme's gem에 저장되어있다.
    Gem-based method는 쉬운 설치를 허락하고, 당신은 여러 테마 파일들의 관리와 같은 업데이트를 할 필요 없다.
    
    To install as a Gem-based theme:
    1. Add the following to your Gemfile :
    
    gem "minimal-mistakes-jekyll"
    
    위 명령어를 터미널에 입력하여 당신의 Gemfile에 따라서 추가해라
    
    2. Fetch and update bundled gems by running the following Bundler command:
    
    bundle
    
    위 명령어를 터미널에 입력하여 Gem 번들들을 패치하고 업데이트 해라
    
    3. Set the theme in your project's Jekyll _config.yml file:
    theme: minimal-mistakes-jekyll
    
    To update the theme run bundle update
    
    위 명령어를 입력하여 당신의 프로젝트의 Jekyll _config.yml 파일을 세팅해라
    
    bundle update 명령어를 입력하여 테마를 업데이트 해라.
    (bundle update를 한 후, git status를 명령해보면 gem이 변화된 것을 확인할 수 있다.)
    
### Remote theme method
    Remote themes are similar to Gem-based themes, but do no require Gemfile changes or whitelisting making them ideal for sites hosted with GitHub Pages.
    원격 테마들은 Gem-based 테마들과 유사하다, 하지만 Gemfile의 변경이나 화이트리스트가 필요하지 않으므로 깃 허브 페이지로 호스팅 되는 사이트에 이상적이다.
    
    To install as a remote theme:
    원격 테마를 설치해보자:
    
    1. Create/replace the contents of your Gemfile with the following:
    아래의 명령어를 따라, 당신의 Gemfile의 내용들을 생성하고/대체해보자.
    (리포지토리를 로컬로 가져오면, 거기에 Gemfile이 들어있다. 거기에 이 텍스트를 넣자.)
    
    source "https://rubygems.org"
    
    gem "github-pages", group: :jekyll_plugins
    gem "jekyll-include-cache", group: :jekyll_plugins
    
    2. Add jekyll-include-cache to the plugins array of your _config.yml
    당신의 _config.yml 리스트의 plugins 파트에 "jekyll-include-cache"를 추가해라.
    (글쓴이는 테마를 이미 가져와서 그런지, 추가되어있었다.)
    
    3. Fetch and update bundled gems by running the following Bundler
    command:
    
    bundle
    
    위 명령어를 터미널에 입력하여 Gem 번들들을 패치하고 업데이트 해라
    
    4. Add remote_theme: "mmistakes/minimal-mistakes@4.24.0" to your 
    _config.yml file. Remove any other theme: or remote_theme: entry.
    당신의 _config.yml 파일에 "mmistakes/minimal-mistakes@4.24.0를 추가해라.
    다른 theme이나 remote_theme은 지워라.
    
    (글쓴이는 
     "# theme                  : "minimal-mistakes-jekyll"
     "# remote_theme           : "mmistakes/minimal-mistakes"
     이렇게 되어있는 부분을 지우고
     remote_theme             :  mmistakes/minimal-mistakes@4.24.0
     를 추가하였다.)
    
    You may also optionally specify a branch, tag, or commit to use by appending an @ and the Git ref (e.g., mmistakes/minimal-mistakes@4.9.0 or mmistakes/minimal-mistakes@bbf3cbc5fd64a3e1885f3f99eb90ba92af84063d). This is useful when rolling back to older versions of the theme. If you don’t specify a Git ref, the latest on master will be used.
    당신은 또한 선택적으로 branch, tag, commit을 @나 Git ref를 글에 덧붙여서 사용하는 것을 명시할 수 있다.
    이것은 테마의 예전 버전들로 되돌릴 때 유용하다. 당신이 Git ref를 명시하지 않았다면, 최근 브랜치가 사용될 것 이다.
    
    Looking for an example? 
    Use the Minimal Mistakes remote theme starter for the quickest method of getting a GitHub Pages hosted site up and running. Generate a new repository from the starter, replace sample content with your own, and configure as needed.
    예시를 찾아볼까?
    Minimal Mistakes remote theme starter를 사용하여 GitHub Pages 호스팅 된 사이트를 가장 빨리 시작하고 실행해보세요. 
    starter에서 새로운 리포지토리를 생성하고, 샘플 내용을 당신의 내용으로 대체하고, 필요에 따라 구성해보자.
    Minimal Mistakes remote theme starter 페이지
    https://github.com/mmistakes/mm-github-pages-starter/generate
    
    Note: Your Jekyll site should be viewable immediately at http://USERNAME.github.io. If it’s not, you can force a rebuild by Customizing Your Site (see below for more details).
    Note: 당신의 Jekyll 사이트는 http://SEO-YJ(깃 허브 닉네임).github.io 링크에서 즉각적으로 볼 수 있다. 그렇지 않으면, 당신은 당신의 사이트를 재정의하여 재구축 하게 만들 수 있다. (자세한 내용은 아래를 보세요.)
    
    If you’re hosting several Jekyll based sites under the same GitHub username you will have to use Project Pages instead of User Pages. Essentially you rename the repo to something other than USERNAME.github.io and create a gh-pages branch off of master. For more details on how to set things up check GitHub’s documentation.
    당신이 같은 GitHub 닉네임으로 여러 개의 Jekyll을 기반으로 하는 사이트들을 호스팅하고 있으면, 당신은 사용자 페이지들 대신에 프로젝트 페이지들을 사용해야 할 것 이다.
    필수적으로 당신은 "깃허브 닉네임.github.io"이름 대신에 다른 이름으로 리포지토리의 이름을 바꿔야하고, master 브랜치에서 gh-pages 브랜치를 따로 생성해야 한다. 설정 방법에 대한 자세한 내용은 깃허브 공식문서를 참조하자.
    
    You can also install the theme by copying all of the theme files1 into your project.

    To do so fork the Minimal Mistakes theme, then rename the repo to USERNAME.github.io — replacing USERNAME with your GitHub username.

    당신은 또한 당신의 프로젝트 안에 files1 테마의 모든 파일을 복붙하여 테마를 설치 할 수도 있다.
    위 방법으로 하려면 Minimal Mistakes 테마를 fork하고, USERNAME.github.io로 리포지토리의 이름을 변경해라 - 당신의 깃허브 닉네임을 USERNAME으로 대체한다.
    내 생각
    1. 필자가 현재 이 방법으로 Minimal Mistakes의 테마를 가져와 블로그를 만들었다.
    
    GitHub Pages Alternatives: Looking to host your site for free and install/update the theme painlessly? 
    Netlify, GitLab Pages, and Continuous Integration (CI) services have you covered. In most cases all you need to do is connect your repository to them, create a simple configuration file, and install the theme following the Ruby Gem Method above.
    깃허브 페이지 대체: 당신의 사이트를 무료로 호스트하고 테마를 쉽게 설치/업데이트 하는 것을 찾고 싶은가?
    Netlify, GitLab pages, 계속적인 통합(CI) 서비스들은 커버해 줄 것이다. 당신이 필요로 할 대부분의 경우는 위 서비스들을 리포지토리로 연결하고, 간단한 구성 파일을 생성하고, 위의 Ruby Gem 메소드를 따른 테마를 설치하면 된다.
    
    Netlify: Netlify는 웹 애플리케이션 및 정적 웹사이트를 위한 호스팅 및 서버리스 백엔드 서비스를 제공하는 샌프란시스코 기반 클라우드 컴퓨팅 회사입니다.
    
    
### Remove the Unnecessary
    If you forked or downloaded the minimal-mistakes-jekyll repo you can safely remove the following folders and files:

    * .editorconfig
    * .gitattributes
    * .github
    * /docs
    * /test
    * CHANGELOG.md
    * minimal-mistakes-jekyll.gemspec
    * README.md
    * screenshot-layouts.png
    * screenshot.png

    당신이 minimal-mistakes-kekyll 리포지토리를 포크하거나 다운로드 했다면, 당신은 다음 폴더들과 파일들을 안전하게 제거할 수 있다.
    
    Note: If forking the theme be sure to update Gemfile as well. The one found at the root of the project is for building the theme’s Ruby gem and is missing dependencies. To properly setup a Gemfile with the theme, consult the “Install Dependencies” section.
    Note: 테마를 포크하는 경우, Gemfile 또한 업데이트 해야 한다. 프로젝트의 루트에서 발견된 것은 테마의 루비 gem을 구축하기 위한 것이고, 종속성이 없을 것이다.
        테마와 함께 Gemfile을 적절히 설정하려면, "Install Dependencies" 섹션을 참조하자.
    
    
## Setup Your Site
Depending on the path you took installing Minimal Mistakes you’ll setup things a little differently.
Minimal Mistakes를 설치하는 경로에 따라, 당신은 약간 다르게 설정할 것이다.

ProTip: The source code and content files for this site can be found in the /docs folder if you want to copy or learn from them.
ProTip: 당신이 소스 코드나 내용 파일들을 복사하거나 배우고 싶으면, 이 사이트를 위한 소스 코드와 내용 파일들을 /docs 폴더에서 찾을 수 있다.

### Starting Fresh
Starting with an empty folder and Gemfile you’ll need to copy or re-create this default _config.yml file. For a full explanation of every setting be sure to read the Configuration section.
빈 폴더와 Gemfile을 가지고 시작하여, 이 기본 _config.yml 파일을 복사하거나, 재생성 해야 한다. 모든 설정에 대한 모든 설명은 Configuration section을 참조하자.

From v4.5.0 onwards, Minimal Mistakes theme-gem comes bundled with the necessary data files for localization. They will be picked up automatically if you have the jekyll-data plugin installed. If you’re hosting on GitHub Pages, you can copy the _data/ui-text.yml file into your repository for the localization feature to work.
4.5.0 버전 이후로, Minimal Mistakes 테마의 gem이 현지화에 필수적인 데이터 파일과 함께 번들로 제공된다.

내 생각
: 버전 4.5.0 이후부터는, Minimal Mistakes에서 gem과 현지화에 필수적인 데이터들을 함께 번들로 제공한다. 
궁금한 점
1. 현지화?
2. gem

gem에 대한 간단한 공부
1. gem은 '루비 라이브러리'이다. 라이브러리는 필요한 기능을 가져와 추가할 수 있다.
2. 여기서 theme-gem(테마 젬)이라고 했다. 
그러면, 테마 기능을 루비 라이브러리로 가져오는 것이겠네? 그러면, 여러 테마들이 루비 라이브러리에 있고, 우리는 그 중에 원하는 테마를 선택하여 루비 라이브러리에서 가져오는 것인가?
3. 인터넷에서 자동 설치된다.
위에서 공부할 때 "Gemfile"에 명시하면, 자동으로 가져온다고 했다. gemfile에 원하는 gem을 명시하면 자동으로 가져오는 것인가?
Gemfile은 텍스트 파일로써, gem "..." 으로 명시되어 있다. 여기에 작성하면, 가져오는 것 같은데....?

당신이 Jekyll-data plugin이 설치되어 있으면 그것들은 자동적으로 선택된다.

내 생각
그것들 = 번들(Minimal Mistakes 테마 gem, 현지화에 필수적인 데이터 파일들)
Jekyll-data plugin이 설치되어있으면, 이것들을 가져온다는 것 같다.

궁금한 점
Jekyll-data plugin은 어디서 설치하지?

만약 당신이 Github 페이지들에서 호스팅하고 있으면, 당신의 리포지토리로 _data/ui-text.yml 파일들을 복사하여, 현지화 기능이 작동하도록 할 수 있다.

내 생각
현재 내 리포지토리는 
아래 깃허브를 포크하여 나의 리포지토리로 가져온 것이다.
https://github.com/mmistakes/minimal-mistakes
이를 클론하여 내 로컬로 가져왔다.
내 로컬 내의 파일들을 확인해보니 _data/ui-text.yml 파일이 담겨있다.

파일을 확인해보니,
User interface text and labels
글씨와 라벨들의 인터페이스를 관리해주는 부분 같다.

여기서 말하는 현지화 기능은 => 블로그의 텍스트, 라벨을 관리해 줄 수 있다.

You’ll need to create and edit these data files to customize them:

_data/ui-text.yml - UI text documentation
_data/navigation.yml - navigation documentation

당신은 이 데이터 파일들을 생성하고 편집하여 당신의 블로그를 커스텀 해야한다.

내 생각
these data files 
1. _data/ui-text.yml - UI text documentation
https://mmistakes.github.io/minimal-mistakes/docs/ui-text/
사이트의 글자, 라벨들을 관리하는 파일

2. _data/navigation.yml - navigation documentation
https://mmistakes.github.io/minimal-mistakes/docs/navigation/
사이트의 이동(다음 페이지, 시작 페이지 등)을 관리하는 파일

### Starting from jekyll new
Scaffolding out a site with the "jekyll new" command requires you to modify a few files that it creates.
"jekyll new" 명령으로 만든 스캐폴딩 기술이 적용된 사이트는 생성된 몇 개의 파일들을 수정하길 요구한다.

Edit _config.yml. Then:

Replace <site root>/index.md with a modified Minimal Mistakes index.html. Be sure to enable pagination if using the home layout by adding the necessary lines to _config.yml.
Change layout: post in _posts/0000-00-00-welcome-to-jekyll.markdown to layout: single.
Remove about.md, or at the very least change layout: page to layout: single and remove references to icon-github.html (or copy to your _includes if using it).
_config.yml파일을 수정한다. 그러면:
<site root>/index.md 파일을 수정된 Minimal Mistakes index.html 파일로 변경한다.
홈 레이아웃을 사용하는 경우, _config.yml 파일에 필수적인 줄들을 추가하여, 페이지 번호 매기기를 활성화해야한다.
레이아웃 변경: _post 폴더 내에 "0000-00-00-welcome-to-jekyll.markdown"파일 형식으로 게시글을 생성: 1개씩
about.md를 제거하거나 가장 최소로 레이아웃 변경은 "layout: page"를 "layout: single"로 변경하고, icon-github.html에 대한 참조들을 제거하라. (사용하는 경우 당신의 _includes폴더에 복사)

내 생각
1. Minimal Mistakes index.html이 로컬 폴더에 저장되어 있다.
2. 번호 매기기는 아직 어떻게 하는지 모르겠다.
3. post폴더에 "0000-00-00-welcome-to-jekyll.markdown"파일 형식으로 1개씩 생성하고 푸시를 진행하면, 블로그에 게시글이 1개씩 생성되는 것을 확인할 수 있다.
4. 현재 _config.yml은 layout: single로 설정되어 있다.

자료
1. 스캐폴딩 기술 정리
https://en.wikipedia.org/wiki/Scaffold_(programming)#Scaffolding_in_Ruby_on_Rails

### Migrating to Gem Version
If you’re migrating a site already using Minimal Mistakes and haven’t customized any of the theme files things upgrading will be easier for you.
만약 당신이 이미 Minimal Mistakes를 사용하여 사이트를 옮기고, 어떠한 테마 파일로도 커스텀하지 않았다면 쉽게 업그레이드 할 수 있다.
내 생각
1. 나는 Minimal Mistakes를 포크하여 사이트를 만들었다.
2. 아직 테마 파일들을 커스텀하지 않은 것 같다.
3. 그러면 업그레이드가 쉽다는데, 버전 업그레이드 말하는 것이겠지?

Start by removing the following folders and any files within them:
다음 폴더들과 폴더 내의 모든 파일들을 제거하는 것 부터 시작해라:

├── _includes
├── _layouts
├── _sass
├── assets
|  ├── css
|  ├── fonts
|  └── js

내 생각
1. 일단 제거해 보았다.

You won’t need these anymore as they’re bundled with the theme gem — unless you intend to override them.
당신에게 테마 gem과 함께 제공되므로 더 이상 위 폴더들이 필요하지 않다
- 당신이 그것들을 무시할 의도가 아니라면
override them 링크
https://jekyllrb.com/docs/themes/#overriding-theme-defaults

내 생각
1. includes, layouts, sass, assets 폴더들은 테마 gem 라이브러리에서 제공이된다.
2. 따라서, 폴더들에 필요하지 않다.

Note: When clearing out the assets folder be sure to leave any files you’ve added and need. This includes images, CSS, or JavaScript that aren’t already bundled in the theme.
Note: assets 폴더를 청소할 때, 당신이 추가하거나 필요로 하는 어떠한 파일들도 없어야 한다.
이것은 테마에 아직 제공되지 않은 사진들, CSS, 또는 JavaScript 파일들을 포함한다.

내 생각
1. 일단 위 폴더 4개 지운후 깃 리포지토리에 푸시하여 테스트 해보았다.
2. 결과는 전과 동일한 블로그 환경이었다.
3. 제거해도 상관 없는 건가?? 어짜피 gem에서 제공이 되니까...?

From v4.5.0 onwards, the default language files are read-in automatically via the jekyll-data plugin if it’s installed. For sites hosted with GitHub Pages, you still need to copy the _data/ui-text.yml file because the jekyll-data plugin is unsupported on GitHub Pages.
4.5.0 버전 부터는, 기본 언어 파일들은 만약 jekyll-data plugin이 설치되어있으면, 이것을 통하여 자동적으로 읽힌다. 깃허브 페이지로 호스팅 된 사이트들은, 당신은 여전히 _data/ui-text.yml 파일을 복사해야 한다. 왜냐하면 jekyll-data plugin이 깃허브 페이지들을 지원하지 않기 때문이다.

내 생각
1. _data/ui-text.yml 파일들은 아직 로컬에 저장되어있다.

If you customized any of these files leave them alone, and only remove the untouched ones. If done correctly your modified versions should override the versions bundled with the theme and be used by Jekyll instead.
당신이 이 파일들 중 하나를 사용자 정의한 경우에는 해당 파일은 그대로 두고, 오직 변경되지 않은 파일만 제거한다. 
올바르게 수정되었으면, 당신의 수정된 버전들은 테마와 함께 번들된 버전들 보다 우선해야하며, 대신에 Jekyll이 사용해야 한다.

내 생각
1. 파일은 본인의 블로그에 맞게 수정한 파일이 있으면 해당 파일은 그대로 둔다.
2. 위 폴더의 파일들 중 변경하지 않은 파일들은 제거한다.
3. 수정한 파일은 우선해야하고 JeKyll이 사용해야 한다.

### Update Gemfile
Replace gem "github-pages or gem "jekyll" with gem "jekyll", "~> 3.5". You’ll need the latest version of Jekyll for Minimal Mistakes to work and load all of the theme’s assets properly, this line forces Bundler to do that.
gem "github-pages" 또는 gem "jekyll"을 gem "jekyll", "~> 3.5"로 대체한다. 당신은 테마의 모든 자료들을 제대로 올리고 작업하려면, Minimal Mistakes의 Jekyll의 최신 버전이 필요할 것이고, 이 줄은 Bundler에게 이렇게 하도록 강요한다.

내 생각
1. 이 문단은 Gemfile 버전을 업데이트 하는 것에 관련있는 것이다.
2. 블로그 테마의 모든 자료들을 제대로 작동하게 하고, 로드하기 위해서는 Jekyll의 최신 버전이 필요하다. 그래서, 이 문단이 gem의 업데이트 방법을 알려주는 것이다.

Add the Minimal Mistakes theme gem:

gem "minimal-mistakes-jekyll"

When finished your Gemfile should look something like this:

source "https://rubygems.org"

gem "jekyll", "~> 3.7"
gem "minimal-mistakes-jekyll"

Then run bundle update and add theme: minimal-mistakes-jekyll to your _config.yml.

Minimal Mistakes 테마 gem을 추가하라: 

gem "minimal-mistakes-jekyll"

완료되면 당신의 Gemfile은 다음과 같이 보일 것이다:

source "https://rubygems.org"

gem "jekyll", "~> 3.7"
gem "minimal-mistakes-jekyll"

그런 다음 번들 업데이트를 실행하고 테마를 추가한다: 당신의 _config.yml 파일에 minimal-mistakes-jekyll을 추가한다.

내 생각
1. 일단 한 번 따라해보자.

minimal-mistakes-jekyll 업데이트 방법
1. Gemfile에 
source "https://rubygems.org"

gem "minimal-mistakes-jekyll"

이렇게 추가하였다.

2. Gemfile에 추가 후에 
터미널에서 해당 폴더로 이동 후, "bundle update"를 명령 하였으나 실패

3. 그냥 "bundle update"를 명령하면, 아래와 같이 해보라고 터머널에서 제시하여
아래의 명령을 순서대로 입력

bundle config set --local path 'vendor/bundle'
bundle update

4. ...
Fetching jekyll-sass-converter 2.2.0
Installing jekyll-sass-converter 2.2.0
Fetching jekyll 4.2.2
Installing jekyll 4.2.2
Fetching jekyll-feed 0.16.0
Fetching jekyll-include-cache 0.2.1
Fetching jekyll-sitemap 1.4.0
Installing jekyll-feed 0.16.0
Installing jekyll-include-cache 0.2.1
Installing jekyll-sitemap 1.4.0
Fetching minimal-mistakes-jekyll 4.24.0
Installing minimal-mistakes-jekyll 4.24.0
Bundle updated!
등의 결과들이 터미널에 나오면서 Gemfile 업데이트 성공

v4 Breaking Change: Paths for image headers, overlays, teasers, galleries, and feature rows have changed and now require a full path. Instead of just "image: filename.jpg" you’ll need to use the full path eg: "image: /assets/images/filename.jpg". The preferred location is now "/assets/images/" but can be placed elsewhere or externally hosted. This applies to image references in _config.yml and author.yml as well.
버전 4부터의 변화: image headers, overlays, teasers, galleries, 그리고 feature rows의 경로들은 변화되었고 이제 전체 경로가 필요하다. 
단지 "image: filename.jpg" 대신에 당신은 (예: "image: /assets/images/filename.jpg")와 같은 전체 경로를 작성하는 것이 필요할 것이다.
선호하는 주소는 "image: /assets/images/filename.jpg"와 같은 형식이지만, 다른 곳에 배치하거나 외부에서 호스트될 수 있다.
이는 또한 _config.yml 파일과 author.yml 파일의 사진 참조에도 적용이된다.

That’s it! If all goes well running bundle exec jekyll servee should spin-up your site.

See "Structure page" for a list of theme files and what they do. ↩

You could also run "bundle update jekyll" to update Jekyll. ↩

다 됐다! 만약 "bundle exec jekyll serve" 명령으로 잘 동작하면 당신의 사이트를 시작할 수 있다.

테마 파일들 및 테마 파일의 작업 목록은 "Structure page"를 참조하세요.

당신은 "bundle update jekyll"을 명령하여 Jekyll을 업데이트 할 수도 있습니다.

내 생각
1. Structure 파이트에 테마 파일 들에 대해 배우자
2. bundle update jekyll 명령을 통해 Jekyll을 업데이트 하자.
