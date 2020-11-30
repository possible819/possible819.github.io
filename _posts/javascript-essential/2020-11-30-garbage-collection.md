---
layout: post
dirpath: "javascript-essential"
title: "About Garbage Collection"
date: 2020-11-30 23:12:00 +0900
category: Posting
tags: [Javascript, Garbage Collection, GC]
thumbnail: "gc.jpg"
summary: "Javascript의메모리 관리"
indexes:
  [
    { id: "what-is-gc", display: "Garbage Collection?" },
    { id: "reference-counting-gc", display: "Reference-counting (참조 세기) Garbage Collection" },
    { id: "mark-and-sweep", display: "Mark and Sweep (표시하고-쓸기) 알고리즘" },
  ]
---

> C 언어와 같은 Low Level Language는 메모리의 관리를 명시적으로 수행한다. malloc(), free()와 같은 function을 호출하는 것이 그에 해당된다. 하지만 Javascript와같은 High Level Language는 더이상 사용하지 않는 메모리의 할당을 자동으로 해제해주며 이것을 Garbage Collection이라한다.

<h4 id="what-is-gc">1. Garbage Collection?</h4>
Garbage Collection은 필요한 메모리를 할당하고 추적하며 더 이상 필요하지 않을 경우 할당된 메모리를 회수하는 역할을 자동으로 수행하는 프로세스를 의미한다. GC는 Javascript와 같은 고수준 언어에서 채택하는 방법으로 개발자로 하여금 메모리 관리에 대한 고민을 덜어 줄 수 있다는 점에서 참 편리한 방법임에 분명하다. 하지만 메모리가 더이상 필을하지 않는지의 여부는 비결정적 GC에 의존하는 메모리 관리 방식은 완벽한 해결책이라고는 할 수 없다.

다음은 Javascript가 수행하는 GC의 기본적인 방법론에 대해 설명한다. 

<h4 id="reference-counting-gc">2. Reference-counting (참조 세기) Garbage Collection</h4>


<h4 id="mark-and-sweep">3. Mark and Sweep (표시하고-쓸기) 알고리즘</h4>

