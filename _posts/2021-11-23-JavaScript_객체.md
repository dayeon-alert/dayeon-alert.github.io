---
title: JavaScript_객체
author: 다연
date: 2021-11-23 21:42:00 +0900
categories: [Study, JavaScript]
tags: [JavaScript, Inflearn]
---
### 객체의 소개와 문법
- 영어로는 object. 
- 연관된 데이터들을 담아내는 일종의 그릇이다.
- 자바스크립트에서 배열과 유사한 역할을 한다.
### 객체와 배열의 차이점
- 인덱스가 자동으로 정해지는 배열과 달리, 객체는 인덱스의 값으로 숫자가 아닌 문자나 원하는 데이터를 사용할 수 있다.
- 다른 언어에서는 연관배열 또는 맵, 딕셔너리라는 데이터 타입이 객체에 해당한다.
- 객체는 객체 지향이라고 하는 프로그램 패러다임과 밀접한 연관이 있다.
#### 객체를 만드는 방법
```
var grades = {}; // var grades = new Object();
grades['egoing'] = 10;
grades['k8805'] = 6;
grades['sorialgi'] = 80;

console.log(grades['k8805'];
// console.log(grades['k88'+'05'];
// console.log(grades.k8805)
// console.log(grades.'k88'+'05')는 SyntaxError 발생
```
### 객체와 반복문
- 배열은 저장된 데이터들이 순서를 갖고 있다.
	- 먼저 들어간 데이터와 나중에 넣은 데이터가 기록되어 있다.
	- 해당 상태가 내부적으로 유지되므로, 넣은 순서대로 꺼내는 것이 가능하다.
- 객체 안에 저장된 값은 순서가 없다. Key와 Value가 한쌍으로 존재한다.
- 객체의 key를 가져올 때 for in문을 사용한다. (배열에서도 동일하게 적용되며, 이 경우는 인덱스 값을 출력)

```
var arr = ['a', 'b', 'c'];
for(var name in arr){
	console.log(name);
} // 0 1 2, 인덱스 값을 출력
```
### 객체 지향 프로그래밍
```
var grades = {
    'list': {'egoing': 10, 'k8805': 6, 'sorialgi': 80},
    'show' : function(){
    // 변수가 가리키는 그릇에 담겨있는 key 값을 하나씩 가져온다.
    // 이 key 값을 name에 담는다. 
        for(var name in this.list){
            document.write("<li>name"+':'+this.list[name]+"</li>");
        }
    }
};
grades.show(); // grades['show']();
```
- graders라는 객체 안 list라는 키값은 다시 객체를 가질 수 있다.
- 객체 내의 value는 객체거나 함수일 수도 있다.
- grades라는 객체에 접근할 때는 grades['list'], grades['list']['egoing'], grades['show']()를 사용. 
- this는 자바스크립트에 약속된 변수로 함수가 속해있는 객체를 가리킨다.
- this는 함수를 어떻게 생성했냐에 따라 달라지지만, 여기서 this는 함수를 소유하고 있는 객체를 의미한다. 
- this.list를 하면 이 객체가 갖고 있는 list라는 key 값이 가리키는 객체를 가리킨다. 
- console.log(this.list); 하면 list가 가리키는 객체가 출력할 수 있으며, alert보다 condsole.log를 사용하는 것이 데이터를 확인할 때 더 편리하다.
- 연관되어 있는 값과 처리를 하나의 그릇 안에 모아서 grouping 해놓은 프로그래밍 기법 스타일을 객체 지향 프로그래밍이라고 한다.
