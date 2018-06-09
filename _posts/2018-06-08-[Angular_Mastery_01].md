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

한 가지 일을 `숙련`시키고싶다.

컴퓨팅 능력 중 하나가 Angualr이다.

# 목차

1. [Applcation Shell](#Applcation-Shell)
2. [The Hero Editor](#The Hero Editor)  


## Applcation Shell

### 요약

```
1. Angular CLI를 사용하여 초기 응용 프로그램 구조를 만들 수 있다.
2. Angular 구성 요소는 데이터를 표시한다는 사실을 알게되었습니다.
3. 보간의 이중 중괄호를 사용하여 앱 제목을 표시했습니다.
```

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

```ts
<--app.component.html-->
<h1>{{title}}</h1>
```

## The Hero Editor   

### 요약  

``sh
1. CLI를 사용하여 두 번째 HeroesComponent를 만들었습니다.
2. HeroesComponent를 AppComponent 셸에 추가하여 표시했습니다.
3. UppercasePipe를 적용하여 이름의 서식을 지정했습니다.
4. ngModel 지정 문을 사용하여 양방향 데이터 바인딩을 사용했습니다.
5. 당신은 AppModule에 대해 배웠습니다.
6. AppModule에 FormsModule을 가져 와서 Angular가 ngModel 지시어를 인식하고 적용하도록했습니다.
7. AppModule에서 컴포넌트 선언의 중요성을 배웠고 CLI가이를 선언했습니다.
```