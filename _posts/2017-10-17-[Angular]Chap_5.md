---
layout: post
title: "[Angular] Chap_5"
description: "Angular 바인딩, 옵저버블, 파이프"
date: 2017-10-17
tags: [Angular Chap_5, 바인딩, 옵저버블, 파이프]
comments: true
share: true
---
최초작성일: 17.10.17  
최종작성일: 17.10.17  
교재: 타입스크립트로 배우는 앵귤러 프레임워크 `한장현|옮김`  

# 목차  

1. 데이터 바인딩의 종류  
2. 어트리뷰트 바인딩 vs 프로퍼티 바인딩  
3. 이벤트를 옵저버블 데이터 스트림으로 처리하기  
4. 불필요한 HTTP 요청을 취소해서 네트워크 부하 줄이기  
5. 파이프 사용 방법  

---

## 1. 데이터 바인딩의 종류  

### 1.1 데이터 바인딩  

- 이벤트 바인딩은 이벤트에 함수를 연결하고, 이벤트가 발생하면 이 함수를 실행한다.  
- 어트리뷰트 바인딩은 HTML 엘리먼트 어트리뷰트에 있는 텍스트 값을 갱신할 때 사용한다.  
- 프로퍼티 바인딩은 DOM 객체 프로퍼티에 있는 값을 갱신한 때 사용한다.  
- 템플릿 바인딩은 뷰 템플릿을 조작할 때 사용한다.  
- 양방향 데이터 바인딩 `ngModel`을 사용한다.  

#### 1.1.1 이벤트 바인딩  

```js
<button (click)="onClickEvent()">Get Products</button>  
<input (input)="onInputEvent()">
```

#### 1.1.2 프로퍼티 바인딩  

```js
<input [value]="myComponentProperty">
```

#### 1.1.3 양방향 바인딩  

```js
<input [value]="myComponentProperty"
  (input)="onInputEvent($event)">
```
하지만 양방향 바인딩을 할 때마다 이렇게 작성하는 것은 비효율적이기 때문에,
Angular에서는 좀 간단한 `[()]` 표기법과 NgModule 디렉티브를 제공한다.  
디렉티브 이름은 NgModel이지만 템플릿에서는 첫 글자를 소문자로 쓰는 것에 주의하자.  

```js
<input [(ngModel)]="myComponentProperty">
```
