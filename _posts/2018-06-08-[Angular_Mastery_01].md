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
2. [The Hero Editor](#The-Hero-Editor)  
3. [Displaying a List](#Displaying-a-List)  
4. [Master/Detail Components](#Master/Detail-Components)  

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

```sh
1. CLI를 사용하여 두 번째 HeroesComponent를 만들었습니다.
2. HeroesComponent를 AppComponent 셸에 추가하여 표시했습니다.
3. UppercasePipe를 적용하여 이름의 서식을 지정했습니다.
4. ngModel 지정 문을 사용하여 양방향 데이터 바인딩을 사용했습니다.
5. 당신은 AppModule에 대해 배웠습니다.
6. AppModule에 FormsModule을 가져 와서 Angular가 ngModel 지시어를 인식하고 적용하도록했습니다.
7. AppModule에서 컴포넌트 선언의 중요성을 배웠고 CLI가이를 선언했습니다.
```

> Create the heroes component  

```
ng generate component heroes 
```

`src/app/heroes/`에 폴더가 생성된다.  

```ts
//heroes.component.ts
//class내부

hero = 'Windstorm';
```
 
```angular2html
<!--heroes.component.html-->

{{hero}}
```

위 작성내용을 보려면

이래 내용을 작성해야한다. 

```angular2html
<!--src/app/app.component.html-->

<app-heroes></app-heroes>
```

## Displaying a List   

> Create a Hero class  

`src/app`에 생성한다.

```js
// src/app/hero.ts

export class Hero {
    id: number;
    name: string;
}

```

```ts
//src/app/heroes/heroes.component.ts

import { Component, OnInit } from '@angular/core';
import { Hero } from '../hero';

@Component({
  selector: 'app-heroes',
  templateUrl: './heroes.component.html',
  styleUrls: ['./heroes.component.css']
})
export class HeroesComponent implements OnInit {
  hero: Hero = {
    id: 1,
    name: 'Windstorm'
  };

  constructor() { }

  ngOnInit() {
  }

}

```

> Show the hero object  

hero 배열안의 값을 반환한다.

```angular2html
<!--heroes.component.html-->

<h2>{{ hero.name }} Details</h2>
<div><span>id: </span>{{hero.id}}</div>
<div><span>name: </span>{{hero.name}}</div>
 
```

> Format with the UppercasePipe  

pipe의 내부함수를 사용할 수 있다.  

```angular2html
<!--heroes.component.html-->

<h2>{{ hero.name | uppercase }} Details</h2>
<div><span>id: </span>{{hero.id}}</div>
<div><span>name: </span>{{hero.name}}</div>

```

> Two way binding  

[(ngModel)]은 angular binding 문법이다.  

```angular2html
<!--src/app/heroes/heroes.component.html-->

<div>
    <label>name:
      <input [(ngModel)]="hero.name" placeholder="name">
    </label>
</div>
```

> Creat mock List  

`src/app`의 영웅 리스트를 만든다.  

```ts 
//src/app/mock-heroes.ts

import { Hero } from './hero';

export const HEROES: Hero[] = [
    { id: 11, name: 'Mr. Nice' },
    { id: 12, name: 'Narco' },
    { id: 13, name: 'Bombasto' },
    { id: 14, name: 'Celeritas' },
    { id: 15, name: 'Magneta' },
    { id: 16, name: 'RubberMan' },
    { id: 17, name: 'Dynama' },
    { id: 18, name: 'Dr IQ' },
    { id: 19, name: 'Magma' },
    { id: 20, name: 'Tornado' }      
];

```


변수 입력. 
```ts
// src/app/heroes/heroes.component.ts 

import { HEROES } from '../mock-heroes';

heroes = HEROES;
```

`<li *ngFor="let hero of heroes">`


> Add the click event handler  

```ts
src/app/heroes/heroes.component.ts  

selectedHero: Hero;  

onSelect(hero: Hero): void {
 this.selectedHero = hero;
}
```

`hero`를 `seletedHero`로 이름을 변경한다.  

> Style the selected hero
  
```angular2html
<!--heroes.component.html (toggle the 'selected' CSS class)-->

[class.selected]="hero === seletedHero"
```

## Master/Detail Components  

> Make the HeroDetailComponent  

detail component를 하나 생성해 재사용하기 쉬운 한 부분을 넣자  
`ng generate component hero-detail`  

```angular2html
<!--src/app/hero-detail/hero-detail.component.html-->

<div *ngIf="hero">

  <h2>{{ hero.name | uppercase }} Details</h2>
  <div><span>id: </span>{{hero.id}}</div>
  <div>
    <label>name:
      <input [(ngModel)]="hero.name" placeholder="name"/>
    </label>
  </div>

</div>

<!--src/app/hero-detail/heroes.component.html-->

<app-hero-detail [hero]="selectedHero"></app-hero-detail>

```

```ts
// src/app/hero-detail/hero-detail.component.ts

import { Component, OnInit, Input } from '@angular/core';

@Input() hero: Hero;
```