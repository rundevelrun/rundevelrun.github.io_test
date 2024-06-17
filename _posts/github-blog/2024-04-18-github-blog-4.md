---
layout: post
title: "[GitHub Pages 4] Jekyll 블로그 RSS 피드 만들기"
category: "github-blog"
tags : [github, pages, blog, jekyll, RSS, SEO]
date : 2024-04-18 14:36:21 +09:00
last_modified_at: 2024-04-19 15:11:18 +09:00
---

이전 포스팅에서 Giscus를 이용한 댓글 기능을 붙였는데 댓글 기능보다 중요한게 있었다.
그것은 바로 댓글 기능이 있어도 이 기능을 사용할 방문자가 없다는 것.
그래서 구글과 네이버에 RSS 피드를 제출해서 검색 엔진에 노출이 되도록 해보려고 한다. 

<blockquote>
  <p>관련글</p>
  <p>
 {% for post in site.categories[page.category] reversed limit:5 %}
    <a href="{{ post.url }}">{{ post.title }}</a> <br>
  {% endfor %}
</p>
</blockquote>


## 1. Jekyll Feed 플러그인 설치

#### 1) Gemfile에 jekyll-feed 추가
- 필자가 사용중인 Hyde 테마에는 이미 추가가 되어 있었다
- 버전에 따라 '_config.yml' 파일 내 plugins 단락에도 추가해줘야하는 경우도 있다

  ![20240418_135458](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/b0993b82-3a5c-4b74-a8c4-ed0003cde488)
{% highlight plaintext%}
gem "jekyll-feed", "~> 0.12"
{% endhighlight%}


#### 2) jekyll-feed 플러그인 설치
- bundle을 이용한 설치
{% highlight plaintext%}
$ bundle install
{% endhighlight%}

- gem을 이용한 설치
{% highlight plaintext%}
$ gem install jekyll-feed
{% endhighlight%}


## 2. RSS 피드를 위한 xml 파일 작성

#### 1) 프로젝트 경로에 xml 파일 생성 
- 필자의 경우 Hyde 테마에 있던 이름을 그대로 사용했다. (atom.xml)

  ![20240417_135716](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/a08102f1-ebfc-4ab1-8543-607c4c34b0b8)

#### 2) xml 파일 내용 수정
- xml 파일의 내용을 아래의 내용으로 변경
{% highlight xml%}
{% raw %}
---
layout: null
---
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:atom="http://www.w3.org/2005/Atom">
  {% assign feed_path = "/feed.xml" %} <!-- 피드경로 명시 -->
  <channel>
    <title> {{ site.title | xml_escape }}  </title>
    <description>{{ site.description | xml_escape }}</description>s
    <link>{{ site.url }}{{ site.baseurl }}/</link>
    <atom:link href="{{ feed_path | prepend: site.baseurl | prepend: site.url }}" rel="self" type="application/rss+xml"/>
    <pubDate>{{ site.time | date_to_rfc822 }}</pubDate>
    <lastBuildDate>{{ site.time | date_to_rfc822 }}</lastBuildDate>
    <generator>Jekyll v{{ jekyll.version }}</generator>
    {% for post in site.posts limit:10 %}
      <item>
        <title>{{ post.title | xml_escape }}</title>
        <description>{{ post.content | xml_escape }}</description>
        <pubDate>{{ post.date | date_to_rfc822 }}</pubDate>
        <link>{{ post.url | prepend: site.baseurl | prepend: site.url }}</link>
        <guid isPermaLink="true">{{ post.url | prepend: site.baseurl | prepend: site.url }}</guid>
        {% for tag in post.tags %}
        <category>{{ tag | xml_escape }}</category>
        {% endfor %}
        {% for cat in post.categories %}
        <category>{{ cat | xml_escape }}</category>
        {% endfor %}
      </item>
    {% endfor %}
  </channel>
</rss>
{% endraw %}
{% endhighlight%}

#### 3) 정상 확인
- github에 push 작업까지 마치면 xml 파일의 이름과 경로에 맞춰서 접속을 해본다.
- https://rundevelrun.github.io/atom.xml (현재 여러분이 보고 있는 블로그의 RSS Feed)

  ![20240417_135938](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/336b60b6-b4cd-4920-9c3a-7f3628d55b6c)


## 3. 검색 엔진에 RSS 피드 제출 (네이버 서치 어드바이저, 구글 서치 콘솔)

#### 1) 네이버 서치 어드바이저
- https://searchadvisor.naver.com/console/board 접속
- 사이트 등록이 되어있지 않다면 사이트 등록을 마친 후 RSS 피드 제출

  ![20240417_135911](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/f2a6d8c8-adde-4897-b30c-9c1165975266)

#### 2) 구글 서치 콘솔
- https://search.google.com/search-console 접속
- 마찬가지로 속성 등록 마친 후 RSS 피드 제출

  ![20240417_135823](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/047e9863-338c-4434-a2da-a38af06c5d6b)



이제 4번째 포스팅이라 검색 엔진이 얼마나 많은 사용자들을 연결해줄지 모르지만 그래도 한단계 나아간 느낌이 든다.
이제 RSS 피드를 제출했으니 다음은 사이트맵을 작성해서 제출해보도록 해야겠다.