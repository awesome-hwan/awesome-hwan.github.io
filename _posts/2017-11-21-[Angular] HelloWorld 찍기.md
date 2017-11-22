---
layout: post
title: "[Angular]Hello World 찍기"
description: "Hello World"
date: 2017-11-21
tags: [angular hello world]
comments: true
share: true
---

처음부터.  

Hello World를 찍어 보았냐, 안찍어보았냐

```sh
> npm install -g @angular/cli  

> ng new my-app  

> cd my-app  

> ng serve --open  
```
기본 설정이 실행된다.  

글자를 바꾸기 위해  

```ts
# src / app / app.component.ts  

export class AppComponent {
  title = 'Hello World';
} 

```
위 내용을 변경하면 `h1`의 내용이 변경된다.  

위 사항으로 알 수 있는것 html과 같이 평범하지 않다.  

의존성이 있다. 

`Focus, 의존성을 생각하며 진행.`  

