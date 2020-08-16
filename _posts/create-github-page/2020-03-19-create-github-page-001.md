---
layout: post
dirpath: "create-github-page"
title: "Github Page 제작기 #001"
date: 2020-03-19 04:08:20 +0900
category: Posting
tags: [Github, Github page, Jekyll]
thumbnail: "github.png"
indexes:
  [
    { id: "create-repository", display: "Repository 생성" },
    { id: "create-index-html", display: "Index.html 생성" },
    { id: "commit-and-push", display: "Commit & Push" },
    { id: "access-website", display: "웹사이트 접속" },
  ]
---

>요즘 사람들은 다양한 SNS를 통해 자신을 표현하듯, 개발자에게 있어 Github는 개발자 자신을 표현기에 가장 직관적인 방법이 아닐까 생각한다. Repository, Profile 등을 통해 개발자 자신이 가지고 있는 관심사를 드러내기도 하는데, 오늘은 Github page 제작을 통해 나와 나의 프로젝트에 대해 소개 할 수 있도록 구성해 보고자 한다.

<h4 id="create-repository">1. Repository 생성</h4>
Github page를 publishing 하기 위해서는 다음의 Format과 동일한 형태의 repository를 생성해야 한다. Github에 로그인 한 뒤 Repository 생성을 진행한다.
`https://github.com/username.github.io`

<h4 id="create-index-html">2. Index.html 생성</h4>
생성한 Repository를 clone 받는다. clone 한 local repository의 내용을 수정하고 push 하는 것으로 github page의 업데이트가 가능하다.

clone을 완료하고 index.html 파일을 생성한다. 해당 파일이 Github page의 entrypoint가 되도록 약속 되어 있는 파일이다.

<h4 id="commit-and-push">3. Commit & Push</h4>
변경 사항을 저장하고 Repository에 commit 및 push 한다.

<h4 id="access-website">4. 웹사이트 접속</h4>
상기의 명시한 Repisotory URL (https://username.github.io)을 브라우저를 통해 열고 접속한다.
index.html을 통해 생성된 화면이 정상적으로 로딩되면 완료!
