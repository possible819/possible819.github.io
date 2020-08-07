---
layout: post
dirpath: "create-github-page"
title: "Github Page 제작기 #002"
date: 2020-03-20 00:00:00 +0900
category: Posting
tags: [Github, Github page, Jekyll]
thumbnail: "jekyll.png"
summary: "Github Page 제작기 - Jekyll 설치 & Scaffolding"
indexes:
  [
    { id: "jekyll-installation", display: "Local 환경에 Jekyll 설치하기" },
    { id: "scaffolding", display: "CLI를 통한 Scaffolding" },
    { id: "check-result", display: "결과 확인" },
  ]
---

지난 포스팅 [[Github page 제작기 #001]](/posting/2020/03/19/create-github-page-001.html)에서 repository 생성 및 Github page의 entrypoint가 되는 index.html 파일의 생성 및 업데이트를 완료했다.

다음으로 Static site generator 중 하나인 Jekyll을 통해 Github page의 구성을 진행 해보자.

진행에 앞서 다양한 Static site generator 중 Jekyll을 사용하는 몇가지가 이유가 있지만 그중 가장 큰이유는 Github가 Jekyll로 구성되어 있는 사이트의 컴파일링을 백그라운드에서 직접 수행해 준다는데 있다. 다시말해 Repository에 컴파일 되지 않은 상태의 markdown을 업로드하면 Github에서 이것을 자동으로 컴파일링하고 정적 웹사이트로 변환해 준다는 것이다.

<h4 id="jekyll-installation">Local 환경에 Jekyll 설치하기</h4>

Jekyll은 Ruby Gem이기 때문에 Local 환경에 설치하기 위해선 Ruby의 설치가 선행 되어야 한다.
아래의 사이트의 가이드를 통해 각 OS 환경에 맞게 설치를 진행한다

[Jekyll 설치 가이드 바로가기](https://jekyllrb.com/docs/installation)

<h4 id="scaffolding">CLI를 통한 Scaffolding</h4>

Jekyll 설치가 정상적으로 완료되면 CLI를 통해 프로젝트 기본 구조를 Scaffolding 할 수 있다.

우선 터미널을 통해 지난 포스팅 [Github page 제작기 #001]에서 생성한 Github Repository 경로로 이동한다.

디렉토리를 변경한 뒤 아래의 명령어를 통해 Scaffolding을 실행 한다.

```bash
  $ jeykell new ./
```

<h4 id="check-result">결과 확인</h4>

브라우저를 통해 자신의 Github Page에 접근하여 결과를 확인한다.
<img src="../../../../assets/create-github-page/sample-page.png">
