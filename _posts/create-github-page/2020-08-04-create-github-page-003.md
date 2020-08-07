---
layout: post
dirpath: "create-github-page"
title: "Github Page 제작기 #003"
date: 2020-08-04 02:24:00 +0900
category: Posting
tags: [Github, Github page, Jekyll, Theme, Layout, Minima]
thumbnail: "theme.png"
summary: "Github Page 제작기 - Theme & Layout"
indexes:
  [
    { id: "find-theme", display: "Theme 파일 찾기" },
    { id: "layout-editing", display: "Layout 수정하기" },
    { id: "style-editing", display: "Style 수정하기" },
  ]
---

Static site generator 중 Jekyll이 가지고 있는 또 하나의 장점은 유연성에 있다.

다른 Static site generator가 제공하지 못하는 혹은 유료 서비스로 제공하는 자유로운 테마의 변경 및 레이아웃 구성이 가능하기 때문이다.

오늘은 기본적으로 제공되는 테마를 자신의 입맛에 맞도록 수정하는 방법에 대해 알아보도록 한다.

<h4 id="find-theme">Theme 파일 찾기</h4>
Jekyll을 통해 초기 구성된 사이트는 Minima라는 이름의 테마를 사용한다.
테마 및 레아이웃의 수정은 사용중인 테마의 소스파일을 찾아 필요한 부분을 오버라이드 하는 것이기 때문에 현재 사용 중인 테마가 어떤 레이아웃을 제공하며 Style sheet는 어떻게 정의 되어 있는지 확인 하는 작업이 선행되어야 한다.

터미널을 통해 다음 명령어를 실행하면 현재 설치되어 있는 테마의 디렉토리를 확인 할 수 있다.

```bash
  # bundle info --path $THEME_NAME
  $ bundle info --path minima
  /home/user/gems/gems/minima-2.5.1
```

<h4 id="layout-editing">Layout 수정하기</h4>
앞에서 확인한 테마의 디렉토리를 편집기를 통해 열어 파일 내용을 확인하면 현재 테마에서 (본 포스팅에서는 Minima) 제공하는 레이아웃을 파악 할 수 있다

<div style="display: flex;">
<img style="margin: auto;" src="../../../../assets/create-github-page/layout.png">
</div>

필요한 내용만 복사하여 내 작업 영역에 `_layouts` 디렉토리를 생성하고 파일을 복사한다.

필요한 내용을 수정하고 저장하여 나만의 레이아웃을 구성할 수 있다.

<h4 id="style-editing">Style 수정하기</h4>

[Layout 수정하기](#layout-editing)와 같은 요령으로 `_sass` 디렉토리를 작업 환경에 생성하고 수정할 scss 파일을 복사한다. 다만 minima.scss 파일에서 다른 스타일의 파일들을 import하고 있기 때문에 사실상 minima.scss 파일만 복사하여 수정하고자 하는 스타일의 css 설정을 override 하면 된다.

미디어 쿼리를 이용한 반응형 웹에 대한 스타일링도 손쉽게 할 수 있도록 되어 있어 간단히 스타일 작업을 수행 할 수 있다.
