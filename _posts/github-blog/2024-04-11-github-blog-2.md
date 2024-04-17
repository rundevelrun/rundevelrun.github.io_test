---
layout: post
title: "[GitHub Blog] 무조건 따라하기 2 - Jekyll 테마 적용"
category: "github-blog"
date : 2024-04-11 16:11:20 +09:00
last_modified_at: 2024-04-17 10:58:46 +09:00
---

이전 포스팅에서는 GitHub의 계정과 Repository를 만들어서 기본 페이지를 웹 브라우저에 띄우는 것 까지 진행해봤는데
블로그로 활용하기 위해서는 정형화된 테마가 필요한데 Jekyll을 이용해서 테마를 적용해볼 예정이다.
선택한 테마는 다를 수 있으나 적용 방법에는 큰 차이가 없으니 도움이 되길 바라며 작성해보겠다. 

> 환경 : Windows 10 Pro

> 관련글
>
> [[GitHub Blog] 무조건 따라하기 1 - 블로그 생성하기](/github-blog/2024/04/05/github-blog-1/) <br>
> [[GitHub Blog] 무조건 따라하기 3 - 댓글/좋아요 기능 만들기 (Giscus)](/github-blog/2024/04/17/github-blog-3/)



## 1. Ruby + DevKit 설치
Jekyll을 활용한 블로그를 로컬에서 구동하기 위해서 Ruby는 필수 요소이다. 필자 Ruby 활용해본 적이 없어서 조금 무서웠다.
하지만 Ruby 문법을 이용해서 대단한 알고리즘을 만들어낸다거나 하는 일은 없으니 안심해도 된다. (그렇다 한들 하면 된다. 할 수 있다.)

#### 1) https://rubyinstaller.org/downloads/ 접속
- <strong>WITH DEVKIT</strong>이라고 적혀있는 단락에서 자신의 시스템에 맞는 최신 버전을 다운로드

  ![20240405_141129](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/ac7952f0-6c4e-4971-b509-17c06483adaf)

#### 2) Ruby Installer 설치
- 별다른 선택 없이 Next 버튼과 OK 버튼의 조합으로 설치

  ![20240405_141224](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/156abaf9-32ac-45c1-a19d-0bf32052124d)


## 2. Jekyll 설치 및 구동


#### 1) Start Command Prompt with Ruby 실행
- 시작 버튼을 누르면 보이는 <strong>Start Command Prompt with Ruby</strong> 실행

  ![20240405_141713](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/ac6cba4d-7977-4a1e-b75e-bf213e3663d1)


#### 2) 설치
- Ruby와 짝꿍인 gem 명령어를 활용해서 Jekyll을 설치한다

  ![20240405_142317](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/b7dcdc68-fafd-4868-84a3-caafc1f4633a)
{% highlight plaintext%}
gem install jekyll
{% endhighlight%}


#### 3) 기본 소스코드 생성 및 확인
- Jekyll 명령어를 활용해서 기본 소스코드를 생성한다. (git clone 디렉토리에서 진행) 
- --force는 붙이지 않아도 된다는 글이 많았지만 필자의 경우 empty 관련 오류가 발생해서 붙여주었더니 해결이 되었다

  ![20240405_142458](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/588ac6cf-a728-465e-b518-109d782eca9d)
{% highlight plaintext%}
jekyll new ./ --force
{% endhighlight%}

- 기본 소스코드 생성 후 디렉토리

  ![20240405_142549](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/0175c54a-d0f8-4ba5-bbe3-4a8a0783f91b)


#### 4) 로컬 서버 구동
- bundle 명령어를 활용해서 테마에 포함된 필수 플러그인을 설치하고 로컬 서버를 구동한다.
- 실행시 빨간색 오류가 발생할 수 있지만 아래와 같은 주소가 표시되면 성공

  ![20240405_143056](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/fff7c279-84bc-422b-a425-cced6da77f00)
{% highlight plaintext%}
bundle install
bundle exec jekyll serve
{% endhighlight%}

- cmd에 표시된 [http://127.0.0.1](http://127.0.0.1)에 브라우저에서 접속하면 드디어 기본 테마가 출력된다.

  ![20240405_143138](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/4c4fd675-7174-4d71-99f8-9401b8e0d029)



## 3. Jekyll 테마 선택 및 적용

#### 1) 테마 선택
- 구글이나 github에서 'jekyll theme'를 검색하면 아주 다양한 테마들을 만날 수 있다.
- 필자가 선택한 테마는 [Hyde](https://jekyllthemes.io/theme/hyde)라는 테마이다. (이름이 찰떡이라 선택했다 : Jekyll and Hyde)
- 테마를 선택한 후 테마의 github repository에 들어가서 Code 버튼을 눌러 압축파일을 다운로드한다.

  ![20240405_143418](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/34e9778e-f00a-45e9-8843-c6826b9b7700)

#### 2) 테마 적용
- 다운로드한 테마의 소스를 작업중인 디렉토리로 덮어쓰기한다.

  ![20240405_143732](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/3b21ea0f-e2ab-42a7-8daf-539ee8fb18c4)

- 파란색으로 선택된 파일을 모두 삭제한다.

  ![20240405_144911](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/76544670-58b7-4ff9-9134-621f631c6b19)

#### 3) 로컬 서버 구동
- 기본 테마를 적용할 때와 같은 명령어를 활용
{% highlight plaintext%}
bundle install
bundle exec jekyll serve
{% endhighlight%}

- 마찬가지로 cmd에 표시된 [http://127.0.0.1](http://127.0.0.1)에 브라우저에서 접속하면 드디어 Hyde 테마가 적용되었다
- CSS를 이용해서 화면을 변경하거나 플러그인을 추가하는 등 다양한 커스텀이 가능하다

  ![20240405_145005](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/686f9083-d3f7-4bec-a93b-8d2b274132bb)


## 4. 운영 서버 적용

#### 1) Repository에 소스 업로드하기 
- git 명령어를 사용해서 GitHub Repository에 소스를 push한다

  ![20240405_140740](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/f8ff3ae8-ed6b-4939-b2d7-df5ff8434b49)
  {% highlight plaintext%}
  git add --all
  git commit -m "테스트 페이지 제작"
  git push origin main
  {% endhighlight%}

#### 2) 정상 확인
- 자신의 블로그 주소로 접속해서 정상 반영 확인 (기본적인 커스텀을 마친 후의 모습)

  ![20240405_151034](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/b5c90f8c-3093-4b70-a8d3-42e467b186a4)



이번 포스팅에서는 깃허브 블로그에 Jekyll을 이용한 테마를 적용해는데
다음은 고맙게 찾아준 여러분과 소통할 수 있는 댓글 기능을 만들어봐야겠다.