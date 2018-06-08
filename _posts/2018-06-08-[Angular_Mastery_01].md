---
layout: post
title: "[Angular_Mastery_01]"
description: "튜토리얼"
date: 2018-06-08
tags: [Anguarl tutorial, 튜토리얼]
comments: true
share: true
---

# 목적

92년~18년 진지하게 몰입해 본 적 없다.
여태 그래왔고 앞으로는 그러기 싫다.

한 가지 일을 `숙력`시키고싶다.

컴퓨팅 능력 중 하나가 Angualr이다.

# 목차

1. Applcation Shell



2.


## Applcation Shell

> install CLI

```
npm install -g @angular/cli #install CLI
```

> Serve the application

```
ng serve --open
```

> Change the application title

`src/app`폴더 확인

app.component.ts- TypeScript로 작성된 구성 요소 클래스 코드
app.component.html- HTML로 작성된 구성 요소 템플릿
app.component.css- 구성 요소의 비공개 CSS 스타일



```ts
//app.component.ts
title = 'Tour of Heroes';
```

```html
<--app.component.html-->
<h1>{{title}}</h1>
```