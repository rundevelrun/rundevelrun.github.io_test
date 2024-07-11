---
layout: post
title: "[React + Vite + Typescript] Storybook 설치하기 (feat. Github Page & Jekyll)"
category:  "react"
tags : [github, pages, blog, react, vite, storybook]
date : 2024-06-17 16:34:48 +09:00
---

최근 UI 관련 프로젝트를 진행하면서 React와 Storybook을 처음 접해보고 지식의 폭(깊이X)을 넓히면서 이해도를 높이기 위해
직접 설치해보면서 Storybook을 구동하고 Github Page에 적용시켜 본 과정을 기록해 보려고 한다.

> 환경 : Windows 10 Pro


## 1. nvm
nvm은 Node Version Manager의 약자로 node.js 버전관리를 위해 설치한다

#### 1) https://github.com/coreybutler/nvm-windows/releases 접속
- 링크 접속 후 하단 'nvm-setup.exe'를 다운로드

  <img alt="20240613_095355" src="https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/2716f885-879b-49bf-a575-ad83f63a516a">

#### 2) 설치 및 확인
- 기본으로 설치 

  <img alt="20240613_095550" src="https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/00acc623-926f-4d3b-93cf-c0590b5c5923">

- PowerShel 혹은 cmd를 열어서 정상 설치 확인

  ![20240613_095709](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/49a41e9f-15ac-4b63-9de0-fc4b42a5d93a)
{% highlight plaintext%}
nvm
{% endhighlight%}

## 2. node & npm
nvm을 이용하여 node 설치 

#### 1) node 설치
- 18 버전으로 설치 후 사용 설정

  ![20240613_100255](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/17a9cab9-46c3-4ff5-b99b-424c289305f1)
{% highlight plaintext%}
nvm install 18 --insecure
nvm use 18
{% endhighlight%}

#### 2) npm strict-ssl 설정 변경
- SSL 인증서 검증을하지 않기위한 설정
- 'self signed certificate in certificate chain' 등의 오류를 방지하기 위한 설정
- npm config list 명령어로 설정 확인

  ![20240613_100350](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/d73c4566-0ffc-4811-a754-0cca8a641e6d)
{% highlight plaintext%}
npm config set -g strict-ssl=false
{% endhighlight%}

## 3. yarn
npm을 이용하여 yarn 패키지를 전역으로 설치한다 (-g 옵션)

#### 1) yarn 설치 및 확인
- yarn 패키지를 설치하고 정상적으로 설치되었는지 확인

  ![20240613_100548](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/2a294805-66e1-402a-a2d2-a4c6999f28ff)
{% highlight plaintext%}
npm i -g yarn
yarn -v
{% endhighlight%}


#### 2) yarn strict-ssl 설정 변경
- 위 npm의 설정과 동일하게 SSL 인증서 검증을하지 않기위한 설정

  ![20240613_100625](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/f10d8033-d5b1-42cd-81cb-634fd7c02742)
{% highlight plaintext%}
yarn config set strict-ssl false
{% endhighlight%}


## 4. Vite
React를 빌드하기 위해 빠르고 간결한 개발을 위한 빌드 도구인 Vite를 활용


#### 1) 의존성 패키지 설치
- npm을 이용하여 create-vite 패키지를 전역으로 설치한다

  ![20240613_101930](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/dfcbbeb0-0848-4bb7-8a8d-3cabf028ce2e)
{% highlight plaintext%}
npm i -g create-vite
{% endhighlight%}

  
#### 2) 템플릿 생성
- Vite 프로젝트명을 입력하고 typescript를 사용하기위해 react-ts 입력

  ![20240613_102044](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/4ed91228-c33f-4676-a8ac-ad0fdcf30ecf)
{% highlight plaintext%}
create-vite [프로젝트명] --template react-ts
{% endhighlight%}


- 입력한 프로젝트명으로 폴더가 생성되면 성공
- 필자의 경우 운영중인 Jekyll 블로그에 포함되도록 설정

  ![20240613_102127](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/347c4460-f95e-47b1-9288-4d069cfd784f)


#### 3) 실행
- 위 명령어를 수행하면 친절하게 다음 순서를 알려준다 ('Done. Now run:' 이하)

  ![20240613_102354](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/0b68f417-330b-487b-9c28-4341622c6aa8)
{% highlight plaintext%}
cd [프로젝트명]
npm install
npm run dev
{% endhighlight%}


- 정상적으로 실행되면 아래와 같이 무언가 해낸 것 같은 화면이 보인다 (이제 시작)

  ![20240613_102847](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/1675b076-3561-400c-8dfb-273f00577672)
  ![20240613_102938](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/23422b99-334c-4927-bde5-4b8a6e854110)


## 5. Storybook
드디어 이 포스팅의 메인인 Storybook을 설치할 차례

#### 1) Storybook 설치 및 초기화
- 패키지를 더 쉽게 설치하고 관리하도록 도와주는 CLI 도구인 npx를 활용해서 Storybook을 초기화

  ![20240613_103407](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/1ffeb35e-5f04-418e-888b-b9f5251e0b0d)
  ![20240613_103521](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/f5f68e92-f609-4c38-8c8c-cc8e55c572c2)
{% highlight plaintext%}
npx storybook@latest init
{% endhighlight%}

#### 2) 실행
- 초기화가 진행된 후 자동으로 Storybook이 실행된다

  ![20240613_103544](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/537e4da6-9cd1-48ab-a888-40abb2df9194)

- 초기화 이후에는 프로젝트 경로 내 package.json 파일에 정의된 script를 이용하여 실행

  ![20240613_103744](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/374ee9e0-cccf-42fc-ac5e-6594099087cf)
{% highlight plaintext%}
yarn storybook
{% endhighlight%}


## 6. Github Pages에 Storybook 올리기 (feat. jekyll)
React + Vite + Typescript를 활용해서 Storybook을 올리기 위한 작업은 위 내용이 끝이지만 필자는 jekyll 테마를 활용해서 Github Pages를 운영하고 있는데 Storybook을 올려서 함께 운영할 예정이다

#### 1) Build 
- 위에도 언급했지만 Jekyll 테마에 Storybook이 포함될 수 있도록 테마 내부에 Vite 프로젝트(storybook-src)를 위치해두었다
- 이제 Storybook을 빌드하면 storybook-src 폴더 내부에 빌드된 파일들이 생성되는데 
  https://[Github Page URL]/storybook 형태로 storybook에 접속하기 위해 package.json의 빌드 경로를 수정했다

  ![20240613_104209](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/1a92834b-c596-40d8-b871-33622a0e70ec)
{% highlight plaintext%}
"build-storybook": "storybook build -o ../storybook"
{% endhighlight%}

- 빌드가 완료되면 경로에 /storybook 폴더가 생성된다 

  ![20240613_104253](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/4b4eb9ea-67b1-4e8b-b437-09f730bad23e)
{% highlight plaintext%}
yarn build-storybook
{% endhighlight%}


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![20240613_104339](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/3def362a-a3bc-47a0-b1a6-2c0f9a3101b2)


#### 2) Jekyll exclude 추가
- bundle exec jekyll serve 명령어를 활용해서 서버에 올릴때 오류를 방지하기 위해서 vite 소스경로를 출력에 포함되지 않도록 _config.xml 수정

  ![20240613_104426](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/5df2aa93-56fd-4f09-93f7-606b729fc6c2)
{% highlight plaintext%}
exclude:
  - storybook-src
{% endhighlight%}


#### 3) Jekyll 테마에 메뉴 등록 (Optional)
- 사용중인 테마의 원하는 곳에 /storybook을 링크하면 끝

  ![20240617_160428](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/b3a5900c-7bfe-46db-a8c5-7ab36cfc0a00)




혼자서 React와 Storybook을 이해하기 위해 설치를 진행해봤는데 이제 React의 Component를 하나씩 구현해보면서 Storybook에 내용을 채워나가봐야겠다