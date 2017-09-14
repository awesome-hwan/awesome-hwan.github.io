---
layout: post
title: "[Angular] Chap_2"
description: "ES6, TypeScript 목차"
date: 2017-09-16
tags: [Angular Chap_2]
comments: true
share: true
---
최초작성일: 17.09.06  
최종작성일: 17.09.14  
교재: 타입스크립트로 배우는 앵귤러 프레임워크 `한장현|옮김`

# 목차  

1. [Angular](#Angular)  
2. [Angular 구성요소](#Angular-구성요소)  
    - [a.모듈(Module)](a-모듈-Module-)
    - [b.컴포넌트(Component)](b-컴포넌트-Component-)  


---
> Why Angular?  

무작정 배우고 싶다.  

# Angular  

> 실행하기  

웹 애플리케이션을 실행하려면 기존적으로 HTTP 서버 필요  

```sh
npm i -g live-server #변경된 코드 브라우저 자동 갱신  

live-server #실행명령어
```

## Angular 구성요소  

### a.모듈(Module)  

모듈은 관련된 컴포넌트나 서비스, 디렉티브 등을 편하게 사용하기 위해 하나로 모은 것이다.  

```ts
@NgModule({
  imports: [BrowserModule],  // 1
  declarations: [HelloWorldComponent], // 2
  bootstrap: [HelloWorldComponent] // 3
})
export class AppModule { }
```

`1. 브라우저를 사용하는 모든 앱은 BrowserModule을 불러와야 한다.`  
`2. AppModule(루트 모듈)에 HelloWorldComponent를 선언한다. 이곳에 선언되는 항목은 애플리케이션 전역에서 사용할 수 있다.`  
`3. 애플리케이션을 실행하면 @NgModule 어노테이션의 bootstrap으로 지정된 HelloWorldComponent가 루트 컴포넌트로 렌더링된다.`  

루트 모듈에서는 반드시 `BrowserModule`을 불러와야 하지만, 루트 모듈을 제외한 다른 모듈에서는 CommonModule을 불러와서 사용한다. 만약 모듈 A를 정의할 때 모듈 B를 불러오도록 지정하면, 모듈 A 안에 있는 모든 컴포넌트들은 모듈B를 자유롭게 사용할 수 있다.  

루트 애플리케이션을 실행하려면 bootstrapModule 모듈을 실행한다.  

`platformBrowserDynamic().bootstrapModule(AppModule);`  

## b.컴포넌트(Component)  

컴포넌트는 Angular 애플리케이션을 구성하는 기본요소, 화면을 정의하는 뷰와 컴포넌트의 동작을 정의하는 클래스로 구성된다.  

컴포넌트는 클래스에 @Component 어노테이션을 붙여서 선언한다.  

```ts
@Component ({
  selector: 'app-component',
  template: '<h1>Hello !</h1>'
})
class HelloComponent {}
```

컴포넌트가 위치할 selector와 렌더링될 내용인 template(또는 templateUrl) 항목은 @Component 어노테이션 안에 반드시 선언되어야 한다.  
