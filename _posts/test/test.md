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
published: true
---

<h4 id="what-is-yeoman">Yeoman?</h4>

Yeoman은 프로젝트 scafollding 도구로 반복적이고 정형화 되어있는 프로젝트 구조를 자동 생성해 주는 node module이다.

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

Generator 작성을 위해 작업할 디렉토리를 생성한다 디렉토리의 명칭은 반드시 `generator-`를 **prefix**로 설정해야 한다 (디렉토리 명칭이 생성할 generator의 모듈 이름과 동일하기 때문에)

```sh
mkdir generator-jekyll-doc
```

아래의 명령줄을 통해 node 패키지를 초기화 한다

```sh
npm init
```

진행되는 질의에 적절한 값을 입력하되 *keywords*항목에 `yeoman-generator`를 입력한다

*package.json*파일 생성이 정상적으로 완료되면 편집기를 통해 해당 파일을 열고 

*files*프로퍼티를 수정해야한다. *files*프로퍼티에는 *generator*에서 사용할 템플릿 파일들을 include 할 경로를 배열의 형태로 나열하면 된다.

상기 keywords 설정은 [Generator 검색](https://yeoman.io/generators){:target="_blank"}에 indexing 되도록 하기 위한 설정으로 필수 조건은 아니다

프로젝트 초기화가 완료되면 `yeoman-generator`를 *dependency*로 추가하여 generator 작성 준비를 한다

```sh
npm install yeoman-generator
```

기타 필요한 *dependency*를 추가한다. 본 예제에서는 아래의 두가지 노드 모듈을 설치하고 사용 했다

```sh
npm install chalk # 터미널에 출력되는 문자의 styling을 도와주는 모듈
npm install moment # Date formatting을 도와주는 모듈
```

>package.json

```json
{
  "name": "generator-jekyll-doc",
  "version": "0.0.1",
  "description": "Yeoman generator for github page",
  "files": [
    "generators"
  ],
  "keywords": [
    "yeoman-generator"
  ],
  "dependencies": {
    "chalk": "^4.1.0",
    "moment": "^2.27.0",
    "yeoman-generator": "^4.11.0"
  }
}
```

*package.json*설정이 완료된 이후 *files*에 포함시킨 디렉토리를 생성한다

```sh
mkdir generators
```

생성한 디렉토리 아래에 디렉토리를 하나 더 추가로 생성한다. 이번에 생성하는 디렉토리의 명칭은 이후 *generator*를 실행할 때 입력하게 될 *argument*가 되기 때문에 어떤 목적의 *generator*인지 확인하기 쉬운 명칭으로 하는 것이 좋겠다.

```sh
cd generators

# 이후 generator를 실행 할 때 yo jekyll-doc:post와 같이 argument로 입력 됨
mkdir post 
```

다시한번 생성한 디렉토리 아래로 이동하여 *templates*라는 명칭의 디렉토리를 생성한다. 해당 디렉토리는 *generator*를 통해 생성하게 될 파일(들)의 템플릿 파일이 저장되는 공간이다.

템플릿 파일은 *ejs*기반으로, *generator*를 통해 전달되는 변수의 값으로 치환되어 최종 파일을 생성하는데 사용된다.

<br>

이제 *generator*의 *entrypoint*가 되는 `index.js` 파일을 생성한다 앞서 생성한 *generators/post*디렉토리 아래에 `yo jekyll-doc:post` 명령을 통해 실행될 *javascript*파일인 *index.js*파일을 생성한다.

<br>

*index.js*에 아래의 코드를 삽입한다.

<br>

>index.js

```javascript
  const Generator = require('yeoman-generator')

  module.exports = class extends Generator {
    constructor(args, opts) {
      super(args, opts)

      this.myPrivateVariable = 'My private variable'

      this.myPrivateFunction = function() {
        console.log(this.myPrivateVariable)
      }
    }

    step1() {
      this.myPrivateFunction()
    }

    step2() {
      console.log('Second step')
    }
  };
```

*generator*는 *return*되는 클래스의 내부 메소드 들을 정의된 순서에 따라 순차적으로 실행한다. *constructor*내부에 생성된 멤버 변수 및 함수들은 실행 대상에서 제외되기 때문에 공통 함수나 변수를 정의하여 사용한다.

`this.prompt` 함수를 호출하여 사용자로 부터 값을 입력 받아 앞서 설명한 *template*파일의 값을 채워 넣을 수 있도록 멤버 변수의 값을 초기화하는 방식으로 *generator*를 작성한다. 보다 자세한 *generator*생성 방법은 아래의 가이드 문서를 참조

<br>

*[Generator 작성 가이드](https://yeoman.io/authoring/index.html){:target="_blank"}*

<h4 id="test-generator">Generator 테스트</h4>

작성중인 *generator*의 테스트를 위해 `npm link`를 이용한다. *generator*작업 영역에서 아래의 커맨드를 통해 *npm link*를 생성한다.

```sh
cd generator-jekyll-doc
npm link
```

*link*가 생성되면 아래의 명령어를 통해 *generator*를 실행한다.
```sh
# yo jekyll-doc:post
yo $GENERATOR_NAME:$TYPE_OF_GENERATOR
```

테스트를 통해 *generator*작성 작업이 완료되면 *npm*에 *publishing*한 뒤 *link*를 제거하고 *global*설치 후 사용 할 수 있다
