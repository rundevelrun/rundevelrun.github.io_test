---
layout: post
title: "리눅스 환경 Swap memory 할당/해제 하기"
categories:  ["linux"]
tags : [linux, centos, swapmemory]
date : 2024-07-04 15:10:18 +09:00
---

로컬에서 개발된 소스를 리눅스 환경에 배포할때 메모리에 관련된 에러 메시지를 자주 만날 수 있다. JVM이나 node 환경에서는 Heap memory를 늘려주는 방법으로도 메모리 관련 에러로부터 자유로울 수 있지만,
물리 메모리가 절대적으로 부족한 상황이라면 디스크의 일부분을 메모리처럼 활용할 수 있는 Swap memory 설정이 해결책이 될 수 있다.

> 환경 : CentOS 8

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


## 1. 개요

#### 1) Swap Memory란?
- 메모리가 가득찬 경우에도 디스크의 일부분을 메모리를 대체할 수 있도록 할당한 공간을 스왑메모리라고 한다

#### 2) Swap Memory 권장 크기
- [Red Hat Enterprise Linux 권장 Swap 크기](https://access.redhat.com/ko/solutions/744483)를 참고하면 Swap 공간을 얼마나 할당해서 사용할지에 대한 답을 찾을 수 있지만 여유 디스크의 사이즈도 고려해서 할당해야 한다


## 2. Swap Memory 할당
WSL CentOS 8 환경에서 8GB의 스왑메모리를 할당해서 사용하려고 한다

#### 1) 메모리 확인
- 할당 전 메로리를 확인해보면 Swap 영역이 '0B'로 잡혀있는 것을 확인 할 수 있다

  ![20240627_134549](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/f3811a3a-5193-45d5-b536-8976ac9e5794)
{% highlight plaintext%}
free -h
{% endhighlight%}

#### 2) Swap file 생성
- fallocate 명령어를 활용해서 할당할 용량의 파일을 생성하고 잘 생성되었는지 확인

  ![20240627_134738](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/8c3e4212-1930-4a20-8afe-e3c8d78e8393)
{% highlight plaintext%}
fallocate -l 8G /swapfile
ls -alh
{% endhighlight%}

- 생성된 파일에 대한 권한 수정

  ![20240627_134919](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/5ea79abf-4f88-4a87-a9c7-75f271b4aad6)
{% highlight plaintext%}
chmod 600 /swapfile
ls -al
{% endhighlight%}

#### 3) Swap 영역 지정 및 활성화
- 스왑 영역 지정
- 출력되는 UUID는 잠시 후 사용해야 하기 떄문에 복사해둔다

  ![20240627_135007](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/ea9e95ec-6a3c-47d3-85f5-87e6d84e1578)
{% highlight plaintext%}
mkswap /swapfile
{% endhighlight%}

- 스왑 영역 활성화 및 확인

  ![20240627_135218](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/93c16c70-bd39-44be-b910-c74f9e8c615e)
{% highlight plaintext%}
swapon /swapfile
free -h
{% endhighlight%}

#### 4) fstab에 파티션 추가
- 앞서 복사해두었던 UUID를 Tab 문자열이나 공백으로 구분해서 '/etc/fstab'에 추가하면 재기동 후에도 유지된다

  ![20240627_135615](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/a504e579-8a5d-41c6-b364-899850bfe90d)
{% highlight plaintext%}
vi /etc/fstab
UUID=c64fddde-dd3d-4829-a3d7-de4d47b8ab76	/swapfile	swap	defaults	0	0
{% endhighlight%}

## 3. Swap Memory 해제
할당을 해봤으니 할당된 영역을 해제하는 방법을 알아보자

#### 1) Swap 영역 비활성화
- 스왑을 비활성화 해주고 생성했던 '/swapfile'을 삭제하면 다시 '0B'로 변한걸 확인할 수 있다

  ![20240627_135810](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/695ba10c-9905-4834-9550-4f549a5e3cc3)
{% highlight plaintext%}
swapoff /swapfile
rm -rf /swapfile
free -h
{% endhighlight%}


#### 2) fstab에 파티션 삭제
- 추가했던 UUID를 제거하면 끝

  ![20240627_135915](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/e89f4d21-63d9-447e-b4f4-e4cf345e8058)
{% highlight plaintext%}
vi /etc/fstab
{% endhighlight%}


이렇게 또 하나의 글감을 발견하고 직접 작업하면서 작성해봤다 