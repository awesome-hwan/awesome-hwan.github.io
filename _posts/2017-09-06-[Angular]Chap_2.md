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
최종작성일: 17.09.16  
교재: 타입스크립트로 배우는 앵귤러 프레임워크 `한장현|옮김`

# 목차  

1. [Angular](#Angular)  
2. [Angular 구성요소](#Angular-구성요소)  
    - [a.모듈(Module)](a-모듈-Module-)
    - [b.컴포넌트(Component)](b-컴포넌트(Component))  
    - [c.디렉티브(Directive)](c-디렉티브-Directive-)
    - [d.데이터 바인딩 기초](d-데이터-바인딩-기초)  

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

## c.디렉티브(Directive)  

디렉티브를 사용하면 HTML 엘리먼트에 사용자가 원하는 동작을 추가할 수 있으며, @Directive 어노테이션을 클래스에 붙여서 선언한다.

```ts
@Directive({
  selector: 'input[log-directive]', // 1
  host: {
    '(input)': 'onInput($event)' // 2
  }
})
class LogDirective{
  onInput(event) { // 3  
    console.log(event.target.value);
  }
}
```

`1. 이 셀렉터가 선택하는 HTML 엘리먼트는 log-directive 어트리뷰트가 있는 input 엘리먼트이다.`  
`2. 호스트 엘리먼트에 입력 이벤트를 연결한다. 이 디렉티브에서 호스트 엘리먼트는 <input> 엘리먼트다.`  
`3. <input> 엘리먼트의 값을 콘솔로 출력하는 핸들러.`  

이벤트 <==> 이벤트 함수 , 이벤트와 이벤트 함수를 연결하려면 이벤트명을 괄호로 감싸면 된다.  

input[log-directive]셀렉터로 선택된 엘리먼트에 입력 이벤트 ('(input)')가 발생하면 onInput() 이벤트가 실행되고, 이떄 $event 객체가 인자로 전달된다.  

`<input type="text" log-directive/> 와 같이 설정한다.`  

## d.데이터 바인딩 기초   

**컴포넌트** 의 프로퍼티 값을 템플릿에 표시하려면 이중 괄호를 사용한다.  
```ts
<h1>Hello {{ name }} </h1>
```  

**컴포넌트 속성** 으로 바인딩 하려면 대괄호를 사용한다.  
```ts
<span [hidden]="isValid">The field is required</span>    
```

**이벤트 <==> 이벤트 핸들러** 연결하려면 괄호를 사용한다.  
```ts
<button (click)="placeBid()"> Place Bid</button>
```
