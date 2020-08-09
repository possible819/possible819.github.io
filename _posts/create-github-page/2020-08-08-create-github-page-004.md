---
layout: post
dirpath: "create-github-page"
title: "Github Page 제작기 #004"
date: 2020-08-08 02:15:53 +0900
category: Posting
tags: [Github, Github page, Jekyll, Yeoman, Generator, Template]
thumbnail: "yeoman.png"
summary: "Github Page 제작기 - Yeoman generator를 통한 posting 템플릿 자동생성"
indexes:
  [
    { id: "what-is-yeoman", display: "Yeoman?" },
    { id: "install-yeoman", display: "Yeoman 설치하기" },
    { id: "create-generator", display: "Generator 작성" },
    { id: "test-generator", display: "Generator 테스트" },
  ]
published: false
---

<h4 id="what-is-yeoman">Yeoman?</h4>

Yeoman은 프로젝트 scafollding 도구로 반복적이고 정형화 되어 있는 프로젝트 구조를 자동 생성해 주는 node module이다.

본 포스팅에서는 Yeoman을 이용해 프로젝트 구조 생성이 아닌 포스팅의 템플릿 파일을 생성 할 수 있는 Generator를 만들어 보도록 한다.

<h4 id="install-yeoman">Yeoman 설치하기</h4>
Yeoman도 하나의 node module이기 때문에 아래의 명령줄을 실핼하여 간단히 설치 할 수 있다.

```sh
# 여러 프로젝트 경로에서 사용하기 때문에 global install
npm install -g yo
```

전역에 설치한 Yeoman은 generator를 실행하기 위한 것이고 Generator는 별도로 설치해 사용하거나 직접 작성하여 사용한다

Generator의 경우에도 마찬가지로 여러 프로젝트 경로에서 사용하기 때문에 global 설치를 기본으로 한다

<h4 id="create-generator">Generator 작성</h4>

Generator 작성을 위해 작업할 디렉토리를 생성한다 디렉토리의 명칭은 반드시 `generator-`를 **prefix**로 설정해야 한다

```sh
mkdir generator-jekyll-doc
```

아래의 명령줄을 통해 node 패키지를 초기화 한다

```sh
npm init
```

진행되는 질의에 적절한 값을 입력하되 `keywords` 항목에 `yeoman-generator`를 입력한다

상기 keywords 설정은 [Generator 검색](https://yeoman.io/generators){:target="\_blank"}에 indexing 되도록 하기 위한 설정으로 필수 조건은 아님

<h4 id="test-generator">Generator 테스트</h4>
본문 (Generator 테스트)
