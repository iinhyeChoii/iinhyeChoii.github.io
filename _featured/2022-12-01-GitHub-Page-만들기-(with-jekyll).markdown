## 1. GitHub Page 만들기

[GitHub Pages](https://pages.github.com/)

## 2. Budler 설정

<aside>
💡 루비와 Bundler가 설치 되어 있어야 합니다.
</aside>

GitHub page 프로젝트 root에서 아래를 실행합니다. (빈 Gemfile로 새 Bundler 프로젝트를 생성)

{% highlight bash %}
bundle init
{% endhighlight %}

옵션 권장 사항 - `./vendor/bundle/` 하위 디렉토리를 만들고 여기에 gem을 설치하도록 Bundler를 설정해줍니다. 
이는 의존 요소들을 고립된 환경에 설치해서, 시스템에 설치된 다른 gem들과 충돌이 발생하지 않도록 보장해줍니다. 

{% highlight bash %}
bundle config set path 'vendor/bundle'
{% endhighlight %}

## 3. Jekyll 추가하기

Bundler를 사용해서 Jekyll gem을 Gemfile 에 추가하고 `./vendor/bundle/` 폴더에 설치합니다.

{% highlight bash %}
bundle add jekyll
{% endhighlight %}

.gitignore 파일에 아래 내용을 추가합니다.

(다른 사용자들은 `Gemfile`과 `Gemfile.lock`에 기반하여 올바른 의존 요소 설치 가능)

{% highlight bash %}
# Jekyll이 생성한 메타 데이터 무시
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata

# Bundler가 생성한 폴더 무시
.bundle/
vendor/
{% endhighlight %}


설치된 Jekyll을 사용해서 사이트를 위한 뼈대를 생성합니다.

{% highlight bash %}
bundle exec jekyll new --force --skip-bundle .
bundle install
{% endhighlight %}

## 4. Jekyll 실행하기

잘 설정이 되었다면 아래 명령으로 웹사이트를 서버에 올리고 [http://127.0.0.1:4000](http://127.0.0.1:4000/) 로 접속할 수 있습니다.

{% highlight bash %}
bundle exec jekyll serve
{% endhighlight %}

## 5. Gemfile 설정

GitHub에서 지원하는 버전으로 맞춰줍니다.

[Dependency versions](https://pages.github.com/versions/)

▴ **GitHub Page Dependency versions**

`gem "github-pages", group: :jekyll_plugins` 부분을 주석 취소 처리 하고,

*`gem "jekyll", "~> 3.9.2"`* 부분을 주석 처리 해주세요.

## 6. _config.yml 설정
title, email, description, url 등을 업데이트 해줍니다.

{% highlight bash %}
title: Your awesome title
email: your-email@example.com
description: >- # this means to ignore newlines until "baseurl:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "" # the subpath of your site, e.g. /blog
url: "https://jekyll.github.io" # the base hostname & protocol for your site, e.g. http://example.com
twitter_username: jekyllrb
github_username:  jekyll
{% endhighlight %}


## 기타 참고 링크
- [💁‍GitHub Page에서 지원하는 테마 리스트](https://pages.github.com/themes/)
- [💁포스트 작성하는 법](https://jekyllrb.com/docs/posts/)
