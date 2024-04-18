---
layout: post
title: "[GitHub Blog] 무조건 따라하기 3 - 댓글/좋아요 기능 만들기 (Giscus)"
category: "github-blog"
tags : [github, pages, blog, jekyll, giscus]
date : 2024-04-17 10:54:55 +09:00
---

이전 포스팅에서는 생성된 블로그에 Jekyll을 활용한 테마를 적용해서 기본적인 CSS, HTML 수정으로 페이지를 꾸며봤다.
이번에는 다른 블로그들에는 기본으로 제공이 되고 있는 댓글 기능을 만들어보려고 한다.
GitHub의 Discussions를 이용하는 [Giscus](https://giscus.app/ko)를 사용할 예정이다.
아쉬운 점은 GitHub에 로그인한 사용자만 댓글을 달 수 있다는 것인데 여기까지 찾아오신 분들이라면 모두 GitHub를 사용할 것이라 문제가 없을 것 같다.

> 관련글
>
> [[GitHub Blog] 무조건 따라하기 1 - 블로그 생성하기](/github-blog/2024/04/05/github-blog-1/) <br>
> [[GitHub Blog] 무조건 따라하기 2 - Jekyll 테마 적용](/github-blog/2024/04/11/github-blog-2/) <br>
> [[GitHub Blog] 무조건 따라하기 4 - Jekyll RSS 피드 만들기](/github-blog/2024/04/18/github-blog-4/) <br>



## 1. GitHub Giscus 앱 설치

#### 1) https://github.com/apps/giscus 접속
- 깃허브에 로그인 후 Giscus 앱 Install 버튼을 클릭

  ![20240411_163515](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/15ba6273-cf0e-4e43-ade7-b21afa9943aa)


#### 2) Giscus 앱을 사용할 Repository 선택 후 설치
- 전체 Repository를 선해해도 좋지만 필자의 경우 현재 GitHub Pages를 사용중인 Repository를 선택했다. 

  ![20240411_163635](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/50dfc2d4-f5b9-4c78-9202-a3542b5e66f0)



## 2. Discussions 활성화
Issues를 사용하는 [Utterances](https://utteranc.es/) 같은 앱은 필요 없겠지만,
Giscus는 Discussions의 활성화가 필수적이다.

#### 1) Repository 설정 화면으로 이동
- Settings 클릭

  ![20240411_164102](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/b6d71987-a177-4a16-9426-25ed5b869e44)


#### 2) Discussions 활성화
- Fetures 단락을 찾아서 Discussions를 활성화해준다.

  ![20240411_164208](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/cb865550-b024-4f2b-b2c5-00eff3af6161)


#### 3) Discussions 탭 생성 확인
- 완료 후 Discussions 탭이 표시되면 정상 

  ![20240411_164257](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/280ebcf9-56de-44fd-a2af-f1cf9a0d63eb)


## 3. Giscus Script 생성
수동으로 Script를 작성해도 되지만 더 간편하게 Script를 생성할 수 있다.

#### 1) https://giscus.app/ko 접속 
- [User이름/Repository이름] 형태로 입력하면 Giscus를 연결할때 조건을 충족하는지 확인할 수 있다.

  ![20240411_164557](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/30d1c140-bdaa-44b7-ba9e-240986b74cb1)

#### 2) Script 생성 확인
- 테마를 선택하는 등 원하는 설정을 모두 마치고 나면 아래와 같은 Script가 자동으로 생성된다.

  ![20240411_164713](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/8f393809-f9b6-4992-8fd4-6f674db1c4c0)



## 4. Giscus Script 적용
드디어 깃허브 블로그에서 댓글과 좋아요 기능을 사용할 수 있는 마지막 관문

#### 1) post.html 파일 수정
- 필자의 경우 Hyde 테마를 사용하고 있어서 post.html 파일을 수정했지만 테마에 따라 파일명은 조금씩 다를 수 있다. (그래도 '_layouts' 폴더 안에 있는 파일이라고 예상된다.)
- 원하는 위치에 Script를 입력한다. 

  ![20240411_170121](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/734a03d5-e3a2-4755-8ff0-af990223ce85)

#### 2) 정상 확인
- 정상적으로 보이면 끝 !

  ![20240411_170304](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/c0df4e2d-e056-44fa-8717-e3432b6580c3)



댓글과 좋아요 기능을 만드는 것도 모든게 수동이지만 직접 만들어가는 GitHub 블로그가 점점 더 애착이 가는 것 같다.
이제 생각나는 부분들은 사용자들이 네이버, 구글 등의 검색 엔진을 통해 들어올 수 있는 SEO, 수익 창출을 위한 광고 노출, 이미지에 Watermark를 자동으로 Overlay하는 기능 등이 있는데
하나씩 구현하면서 포스해보도록 하겠다.
깃허브 블로그 만들기 포스팅이 끝나면 어떤걸 올릴지도 고민해봐야겠다..