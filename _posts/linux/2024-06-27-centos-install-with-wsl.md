---
layout: post
title: "윈도우 환경에 리눅스 개발환경 구축 (CentOS 8)"
categories:  ["linux", "windows"]
tags : [linux, centos, wsl, windows]
# date : 2024-06-27 14:10:13 +09:00
---

개발자라면 한번쯤은 Linux 환경의 연습장이 필요할 때가 있다. 하지만 AWS 등의 Cloud 환경은 부담스럽고
가지고 있는 PC를 밀어버리고 설치하자니 활용도가 낮은 상황이 발생한다. 그래서 Windows 환경에서 CentOS를 사용해보려고 한다.

> 환경 : Windows 10 Pro

{% if site.categories[page.category].length() %}
<blockquote>
  <p>관련글</p>
  <p>
 {% for post in site.categories[page.category] reversed limit:5 %}
    <a href="{{ post.url }}">{{ post.title }}</a> <br>
  {% endfor %}
</p>
</blockquote>
{% endif %}


## 1. WSL
WSL(Windows Subsystem for Linux) 윈도우 환경에서 리눅스 실행 파일을 사용하기 위한 호환성 계층

#### 1) Windows 기능 켜기/끄기 실행
- WSL을 활성화하기위해 Windows 기능 켜기/끄기를 실행

  ![20240627_130211](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/e592fd7a-52ea-414d-b370-dcfaeda63eb6)


#### 2) WSL 활성화
- Linux용 Windows 하위 시스템 체크 후 확인

  ![20240627_130344](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/4ec724e6-3d29-433a-9c87-c0fdc70a63c2)



## 2. CentOS 8
Microsoft Store에서 다양한 WSL용 OS를 설치할 수 있지만 CentOS는 아쉽게 무료버전이 없기 때문에 다른 경로로 설치

#### 1) WSL용 CentOS 8 다운로드
- [https://github.com/mishamosher/CentOS-WSL/releases/tag/8.4-2105](https://github.com/mishamosher/CentOS-WSL/releases/tag/8.4-2105)gi

  ![20240627_130545](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/1abcc23d-e038-4dec-9b50-5cb616f339d5)

- 다운로드 받은 파일을 압축해제 후 이거다 싶은 파일을 실행

  ![20240627_133514](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/dcbdd0b9-d200-4b24-9d94-0b60a25fdb0e)


#### 2) 설치
- 아무키나 누르라고 할때 아무키나 누르면 놀랍게도 설치가 완료된다

  ![20240627_133553](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/7ac4bfe9-7cf6-4e54-89f1-d26722c09e22)

#### 3) 실행
- 설치된 CentOS8을 찾아서 클릭

  ![20240627_133728](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/ef5d75ba-ba8f-444c-b56e-2bebb44ae109)

- 아주 간단한 방법으로 Windows 환경에 CentOS 연습장이 만들어졌다

  ![20240627_133759](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/4a81eb29-29a0-425a-b547-352769c99b73)



블로그에 계속 의미 없이 카테고리만 늘려가는 느낌이 드는데 언젠가 내용을 채울 수 있겠지...