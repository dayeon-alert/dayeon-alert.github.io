---
title: JavaScript_함수
author: 다연
date: 2021-11-11 22:46:00 +0900
categories: [Study, JavaScript]
tags: [JavaScript, Inflearn]
---
### 함수
함수(function)란 하나의 로직을 재실행 할 수 있도록 하는 것으로 코드의 **재사용성**을 높여준다.

### 함수의 형식
함수의 형식은 아래와 같다.  
```
function 함수명([인자...[,인자]){
	코드
	return 반환값
}
```
### 함수의 정의와 호출
```
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<script type="text/javascript">
	function numbering(){ // 함수 정의
		i = 0;
		while(i<10){
			document.write(i+"<br />");
			i += 1;
		}
	} 
	var a = 1; // 변수 정의
	alert(a); // 변수 호출
	numbering(); // 함수 호출, 괄호가 없다면 JavaScript는 변수로 인식한다.
	numbering(); // numbering() 내부의 코드 실행 
	numbering();
	numbering();
	numbering();
	numbering();
	</script>
</body>
</html>
```
### 함수의 효용성
```
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<script type="text/javascript">
	function numbering(){ // 함수 정의
		i = 0;
		while(i<10){
			document.write(i+"<br />");
			i += 1;
		}
	} 
	for(var i=0; i < 1000; i++){ 
		numbering(); // 함수를 1000번 실행
	}
	</script>
</body>
</html>
```
- 반복문 : 함수와 마찬가지로 어떠한 로직을 반복적으로 재사용할 때 사용.
	- 하지만 함수와 비교했을 때 함수와 반복문이 갖고 있는 효용은 다르다.
	- 반복문은 기계적으로 일정한 반복을 그 자리에서 실행할 때 의미가 있다.
- 함수 : 반복적으로 실행되는 로직이 여러가지 맥락에서 반복적으로 쓰이는 경우 의미가 있다. 어디든 호출한 곳에서 실행이 가능하다.


- **재사용성**의 핵심은 동일한 코드가 있을 때 해당 코드를 여러 곳에서 사용할 수 있는 형태로 만드는 것. 좋은 부품을 만드는 것이 재사용성의 목표다.
- 재사용성이 높아지면  함수의 내용(코드)을 수정, 변경, 개선해 문제 해결을 할 경우, 해당 함수를 사용하는 모든 곳에서 반영이 된다다. 이러한 특성을 **유지 보수(maintenance)가 용이**하다라고 한다.
- 그리고 코드의 **가독성**이 좋아진다.
- **재사용성, 유지보수의 용이, 가독성**은 비례 관계이다. 프로그래밍이 발전하는데 있어 가장 핵심적인 개념으로, 이것들이 잘 만들어져 있지 않다면 수정하기 힘든 프로그램이 되고, 쉽게 버그가 발생해 심각한 문제를 야기할 수 있다. 
- 따라서 프로그램에서 이러한 것들은 매우 중요하고, 프로그램의 발전 방향성은 이 세가지에 있다고 할 수 있다.
- 객체 지향 등 문법적인 것들을 만났을 때 이런 것들을 어떻게 극복하는지를 중점적으로 봐야 한다.

## 함수의 입력
- 서양권에서 function은 기능, 작용이라는 의미. 동양권에서 함수의 함은 상자 함이다.
	- 상자 함을 사용하게 된 동기로는 "영어에서 function이라 한 것을 함수라는 소리로 옮길 수 있다. (음역)"라는 주장과, 함수라는 상자가 있고, 그 상자 안에 값을 넣으면 다른 결과가 출력되는 상자라는, funcion의 본질적인 의미를 반영한 창조적인 단어라는 주장도 있다. 
- 입력에 따라 출력이 달라진다. (Function Machine)

## 입력과 출력
```
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<script type="text/javascript">
	function get_member1(){
		return 'egoing'; // 출력
		return 'leezche';
		return 'graphittie';
	}
	function get_member2(){
		return 'k8805';
	}
	
	alert(get_member1());
	alert(get_member2());
	</script>
</body>
</html>
```

- 첫번째 return 뒤에 나오는 코드는 동작하지 않는다. 
- 출력은 내부적으로 return을 통해 출력된다.

```
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<script type="text/javascript">
	// arg는 매개**변수**(parameter), 값을 받는 변수.
	function get_argument(arg1, arg2){ 
		return arg1 + arg2; // return은 출력
	}
	// arg1 = 10, 이 때 arg1로 전송된 값인 10을 인자(argument)라고 부른다. 값 자체는 인자다.
	alert(get_argument(10, 20)); 
	alert(get_argument(20, 30));
	</script>
</body>
</html>
```
- 여러개의 입력값을 받을 수 있지만 return값은 한 개만 가능하다.

## 다양한 정의 방법

```
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<script type="text/javascript">
	var numbering = function(){ // numbering이라는 변수가 함수를 갖게 된 것. 
		i = 0;
		while(i < 10){
			document.write(i);
			i += 1;
		}
	}
	/*
	function numbering(){
		i = 0;
		while(i < 10){
			document.write(i);
			i += 1;
		}
	}
	*/
	// 이렇게 선언하면 상단 두 종류의 코드는 동일하다.
	numbering();
	
	// 함수를 정의한 후 괄호로 묶었다.
	// 이후 함수를 호출할 때 사용하는 기호 ();를 사용,
	// 따라서 함수를 정의하는 것과 정의된 함수를 호출하는 것이 한 문장에 들어간다.
	// 이를 익명함수라 한다. 이름이 없고 바로 실행되는 함수다.
	// 일회성으로 호출할 때 이런 techin을 사용한다.
	// 요약 : 정의와 호출이 동시에 가능한 함수.
	
	(function(){
		i = 0;
		while(i < 10){
			document.write(i);
			i += 1;
		}
	})(); 
	</script>
</body>
</html>
```

- 함수는 코드의 재활용성을 높여준다.
- 자바스크립트를 함수영 언어라고 표현하기도 한다. 그 언어를 규정짓는 특징으로 함수를 사용할 정도로 자바스크립트는 함수가 차지하는 위상이 높다. 
