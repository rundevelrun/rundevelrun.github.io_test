---
layout: post
title: "[GitHub Pages 5] 검색 최적화를 위한 사이트맵 제출하기"
category: "github-blog"
tags : [github, pages, blog, jekyll, sitemap, SEO]
date : 2024-04-19 14:17:16 +09:00
last_modified_at: 2024-04-19 15:11:18 +09:00
---

지난 포스팅에서는 구글 서치 콘솔과 네이버 서치어드바이저에 RSS Feed를 제출했는데
RSS와 함께 필수로 제출해야하는 사이트맵을 제출하려고한다. 사실 이 방법은 RSS 링크를 만드는 것과 거의 동일지만
사이트맵 제공을 위한 xml 파일을 직접 만들고 수정하지 않아도 된다는 점은 다르다.

<blockquote>
  <p>관련글</p>
  <p>
  {% for post in site.related_posts reversed limit:10 %}
    <a href="{{ post.url }}">{{ post.title }}</a> <br>
  {% endfor %}
</p>
</blockquote>


## 1. Jekyll sitemap 플러그인 설치

#### 1) Gemfile 수정
- 먼저 Gemfile을 열어서 jekyll-sitemap을 추가한다.

  ![20240417_133141](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/fe544bae-901d-4e6f-8bd9-f7a570dbd9e0)

{% highlight plaintext%}
gem "jekyll-sitemap"
{% endhighlight%}

#### 2) _config.yml 파일 수정
- _config.yml에 plugins 단락(없으면 추가)에 jekyll-sitemap을 추가한다.

  ![20240419_140635](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/44ccdcf3-237d-460c-b521-af4aafeb6b00)


#### 3) 플러그인 설치
- bundle을 이용한 설치
{% highlight plaintext%}
$ bundle install
{% endhighlight%}

- gem을 이용한 설치
{% highlight plaintext%}
$ gem install jekyll-sitemap
{% endhighlight%}

  ![20240417_133027](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/7142b910-183a-4279-aa83-cc86ccae1006)

#### 4) 정상 확인
- github에 push 작업까지 마친후 [블로그 URL]/sitemap.xml에 접속 
- 예시) https://rundevelrun.github.io/sitemap.xml

  ![20240417_133353](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/9db76b4e-3b1d-4179-92fe-24801d3cca2e)


## 3. 검색 엔진에 사이트맵 제출 (네이버 서치 어드바이저, 구글 서치 콘솔)

#### 1) 네이버 서치 어드바이저
- https://searchadvisor.naver.com/console/board 접속
- RSS 피드를 제출하는 것과 거의 동일

  ![20240417_134728](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/0a1345be-0f2a-4ac3-9ec6-d1e8481b8279)


#### 2) 구글 서치 콘솔
- https://search.google.com/search-console 접속
- 사이트맵 제출

  ![20240417_134509](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/2939b83d-c7c0-42e2-a258-e4657c0fc050)



지금까지 블로그에 Jekyll 테마를 입히고 댓글 기능을 붙이고 또 검색을 위한 RSS와 사이트맵을 만들어 제출했다. 
구글 애널리틱스를 붙여서 실제로 검색을 통한 방문자가 있는지 체크하는 중인데 거의 없는 것 같고 아직 검색도 잘 안되는 것 같다.
그래도 언제나 꾸준함은 답이기 때문에 곧 이어질 포스팅은 구글 애널리틱스와 구글 애드센스를 순차적으로 작성해보겠다.