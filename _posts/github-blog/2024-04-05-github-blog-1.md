---
layout: post
title: "[GitHub Blog] 무조건 따라하기 1 - 블로그 생성하기"
category: "github-blog"
date: 2024-04-05 17:47:38 +09:00
last_modified_at: 2024-04-17 10:58:23 +09:00
---

네이버, 티스토리, 벨로그 등 여러가지 블로그들을 경험하고 운영해왔지만 개발자라면 역시 관심을 가질 수 밖에 없는 GitHub Blog, 
정확히는 [GitHub Pages](https://pages.github.com/)를 경험하고 싶어졌다.
다른 블로그들과는 다르게 개설하는 것 부터 어려움의 연속이기 때문에 첫 게시글로 그 어려움을 순차적으로 공유해보려고 한다.

> 환경 : Windows 10 Pro

> 관련글
>
> [[GitHub Blog] 무조건 따라하기 2 - Jekyll 테마 적용](/github-blog/2024/04/11/github-blog-2/)  <br>
> [[GitHub Blog] 무조건 따라하기 3 - 댓글/좋아요 기능 만들기 (Giscus)](/github-blog/2024/04/17/github-blog-3/)



## 1. Git 설치
GitHub Blog는 기본으로 [GitHub](https://github.com/)의 Repository를 이용하기 때문에
운영을 위해 필수로 설치해야 하는 것 중 하나다.

#### 1) https://git-scm.com/download 접속
- 링크 접속 후 각자의 환경에 맞는 OS를 클릭 (필자의 경우 Windows)

  ![20240405_111300](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/c9773b64-16ca-4b88-be27-8999a0e4af2c)

#### 2) Git Installer 다운로드
- 최신버전 다운로드
  
  ![20240405_111836](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/1bac5347-57db-4488-a000-b7ffbc034568)

#### 3) 설치 및 확인
- 설치는 변경 없이 기본으로 Next 버튼과 OK버튼만 활용해서 끝내버렸다.
- 버전을 명령어로 정상적으로 출력되는지 확인

  ![20240405_112054](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/55986d21-6c61-4fd5-8796-d48dc5a46676)
{% highlight plaintext%}
git -v
{% endhighlight%}


## 2. GitHub 가입 및 Repository 설정

#### 1) GitHub 가입
- https://github.com 에서 일반적인 가입 절차를 따르면 되는데 아래 이미지의 <strong>username</strong>이 블로그의 주소가 된다. (가입 후 변경 가능)

  ![20240405_163711](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/fc36d1f3-5ce8-4805-8ac4-03dd097e6181)

#### 2) Repository 설정
- GitHub에 로그인 후 대시보드에서 New 버튼을 클릭

  ![20240405_110457](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/f9ed72f6-cc6f-4cde-8ee8-ab0270b8ee6e)

- Repository name은 [username].github.io로 입력하고 Add a README file을 체크

  ![20240405_110905](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/7026ac0d-6ff6-4ff6-84a1-32fcbb4420aa)


## 3. Repository 복제 및 테스트 페이지 제작 

#### 1) 개발 환경으로 Repository 소스 복제하기
- 생성한 Repository 화면에서 Code 버튼을 클릭 후 주소를 복사

  ![20240405_112332](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/8af569b6-f858-41ea-95cc-aa47d110d657)

- 명령 프롬프트(cmd)를 열어서 복제할 위치로 이동 (필자의 경우 C:\workspace)
{% highlight plaintext%}
  cd C:\workspace
{% endhighlight%}

- Repository 소스 복제

  ![20240405_112458](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/b5dc2ee7-779f-4664-911f-328a91251ee8)

{% highlight plaintext%}
git clone [복사한 Repository 주소]
{% endhighlight%}

- 복제가 완료되면 Repository의 이으로 폴더가 만들어진다.

  ![20240405_112725](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/e06dd588-deea-4b4c-8deb-8a52d1a66da5)


#### 2) 테스트 페이지 제작
- 내려받은 소스 경로에 index.html 파일 생성

  ![20240405_140225](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/f5174443-088c-49c5-81af-75e2f2a9522e)

- index.html 내용 수정 (이해를 돕기위한 내용이므로 간단하게 텍스트만 입력해도 좋다)

{% highlight html%}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>런:디벨:런</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Diphylleia&display=swap" rel="stylesheet">
    <style>
        .title {
            font-family: "Diphylleia", serif;
            font-weight: 400;
            font-style: normal;
            font-size: 50px;
            text-align: center;
            width: 100%;
            margin-top: 20px;
        }
    </style>
</head>
<body>
<p class="title">런:디벨:런</p>
</body>
</html>
{% endhighlight%}


## 4. 수정사항 반영

#### 1) Repository에 소스 업로드하기 (push)
- git 명령어를 사용해서 GitHub Repository에 소스를 push한다.

  ![20240405_140740](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/f8ff3ae8-ed6b-4939-b2d7-df5ff8434b49)
{% highlight plaintext%}
  git add --all
  git commit -m "테스트 페이지 제작"
  git push origin main
{% endhighlight%}

#### 2) 정상 확인
- 자신의 블로그 주소로 접속해서 정상 반영 확인

  ![20240405_140923](https://github.com/rundevelrun/rundevelrun.github.io/assets/40383414/3cea8ac2-5af9-4af0-96db-445987cd90c5)




다른 블로그였다면 가입하고 테마를 선택하고 관리 기능을 사용해서 글을 쓰면 끝인데 모두 수동으로 해줘야하는게 어렵지만 뿌듯한 마음이 든다.
다음 포스팅에서는 jekyll을 활용한 테마를 적용하는 방법을 작성해봐야겠다.

