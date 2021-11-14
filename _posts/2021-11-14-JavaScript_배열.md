---
title: JavaScript_배열
author: 다연
date: 2021-11-14 23:52:00 +0900
categories: [Study, JavaScript]
tags: [JavaScript, Inflearn]
---
### 배열
- 배열이란 연관된 데이터를 모아 통으로 관리하기 위해 사용하는 데이터 타입이다.
- 변수 : 데이터를 담는 그릇으로, 하나의 그릇에 하나의 데이터만 넣을 수 있다.
- 배열 : 역시 데이터를 담는 그릇이나, 하나의 그릇에 여러 데이터를 넣을 수 있다.
### 배열의 생성
- 대괄호([])는 배열을 만드는 기호.
- 대괄호 안에 데이터를 콤마(,)로 구분해서 내열하면 배열이 된다.
``` Chrome Browser
> var member  = ['egoing', 'k8805', 'sorialgi']
> undefined

> member
> ["egoing", "k8805", "sorialgi"]
```
- var member1 = "egoing"; 같은 식으로 변수에 하나의 값을 담았으나, 배열을 사용하면 하나의 변수 안에 여러 개의 데이터를 담을 수 있게 된다.
- 배열에 들어 있는 각각의 데이터를 원소(Element)라고 부른다.
```
var member = ['egoing', 'k8805', 'sorialgi']
alert(member[0]);
alert(member[1]);
alert(member[2]);
```
- 배열 안 각각의 데이터를 원소라고 하며, 이들은 각각 고유한 식별자를 갖는다.
- 순서대로 0, 1, 2. 자바스크립트가 내부에서 자동으로 부여하는 값으로 한국어로 색인, 영어로는 인덱스라고 한다.
- 대괄호에 인덱스 번호를 전달하면 해당 인덱스에 해당하는 값을 반환한다.
- 프로그래밍은 숫자를 0부터 넘버링한다는 것을 잊지 말 것.
### 배열의 효용성
- 하나의 함수는 하나의 값만을 반환할 수 있기 때문에 배열을 사용하지 않으면 각각의 값을 반환하는 함수를 만들어야 한다.
```
function get_members(){
	return ['egoing', 'k8805', 'sorialgi'];
}
var members = get_members();
document.write(members[0]);
document.write(members[1]);
document.write(members[2]);
```
- 배열은 연관되어 있는 정보를 한꺼번에 다룰 수 있게 하므로 프로그래밍에 있어 중요한 수단이다.

### 배열의 사용
```
function get_members(){
	return ['egoing', 'k8805', 'sorialgi'];
}
var members = get_members();
for(let i = 0; i<member.length; i++){
	document.write(members[i].toUpperCase() + "<br />");
}
```
### 배열의 조작 - 추가
```
var li = ['a', 'b', 'c', 'd', 'e'];
li.push('f');
alert(li); // ['a', 'b', 'c', 'd', 'e', 'f'];
// concat 안에 담겨있는 배열과 li 배열을 연결
// 하나의 배열로 만들어 return하고 그 값을 li에 담는다.
li = li.concat(['f', 'g']);
```
```
var li = ['a', 'b', 'c', 'd', 'e'];
li.unshift('z');
alert(li); // ['z', 'a', 'b', 'c', 'd', 'e'];
```
```
a = ["a", "b", "c"]
// 배열명.splice(index, howmany, element1, ..., elementN)
// 배열의 중간에 추가
// howmany : 해당 인덱스에서 제거되는 원소의 개수
a.splice(1, 1, 'x', 'y'); // ['a', 'x', 'y', 'c']

var myFish = ['angel', 'clown', 'trumpet', 'sturgeon'];
var removed = myFish.splice(0, 2, 'parrot', 'anemone', 'blue');
// ["parrot", "anemone", "blue", "trumpet", "sturgeon"]
```
### 배열의 조작 - 제거, 정렬
```
var li = ['a', 'd', 'b', 'c', 'e'];
li.shift();
alert(li); // ['d', 'b', 'c', 'e'];
li.pop();
alert(li); // ['d', 'b', 'c'];
li.sort(); // ['b', 'c', 'd'];
li.reverse(); // ['d', 'c', 'b'];
```
