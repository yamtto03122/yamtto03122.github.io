---
title: JS operator
tags: [javascript, operator, 기본개념]
style: fill
color: warning
description: 자바스크립트 연산자 학습
toc: true
toc_sticky: true
date: 2023-08-02
last_modified_at: 2023-08-02
published: true
---
기본적인 산수 연산자는 더하기, 빼기, 나누기, 곱하기이다.<br>
스크립트에 새로 추가되는 연산자 : 남는 값(%), 거듭제곱(**)

<br>

### 1. 기본 연산자

```javascript
console.log(10 % 3) // 모두 나눠지면 0, 나눠지지 않으면 1만 남기 때문에 조건식으로도 이용할 수 있다.
console.log (5 ** 3) //결과 : 15 * 15 = 125
console.log('1' + 1) //결과 : '' 안의 수는 문자열로 인식되어 문자열 '11'이 된다. (강제 항변환)
console.log(2 + '1') //결과 : string '21'
```
`''` 안의 수는 문자열로 인식되어 `string`이 된다. (강제 항변환)

<br>

### 2. 복합 연산자

``` javascript
let a = 2;
console.log(a += 3) //함축 a = a + 3 //결과 : 5
console.log(a -= 3) //함축 a = a - 3 //결과 : 2
console.log(a *= 5) //함축 a = a * 5 //결과 : 10
console.log(a %= 3) //함축 a = a % 3 //결과 : 1
```
함축식을 더 많이 사용하는 편이라고 한다...<br>
+, -, /, * 등등 이해가 잘 가는데.. +=는 매번 헷갈린다 ㅠㅠ<br>
그래서 정리를 해보았다..!

> ##### 함축식 이해하기

```javascript
let num1 = 2;

num1 = num1 + 2;
console.log(num1); //num1은 2 + 2가 되어서 4가 나온다.

//// 이것을 함축형으로 바꾸면
num1 += 2; // 자기자신 num1(초기값)에다가 2를 더한다는 의미
console.log(num1); //결과 : 4
```
결국은  num1 + 2  라는 의미..

<br>

### 3. 증감(증가 / 감소) 연산자
> ##### 증가 연산자 `++`
피연산자를 증가(1을 더함)시키고 연산자의 위치에 따라 증가하기 전이나 후의 값을 반환합니다.

> ##### 감소 연산자 `--`
피연산자를 감소(1을 뺌)시키고 연산자의 위치에 따라 감소하기 전이나 후의 값을 반환합니다.

``` javascript
let a = 1;
++a; //a = a + 1
--a; //전위 연산자
console.log(a) //결과 : 1

let b = 2;
b++ //후위 연산자
console.log(b) //결과 : 3

let c = 1;
let result;
result = c++; //1,2
//result = ++c; 2,2
console.log(result, c) //결과 : 1 2
```

> ##### 후위연산자 `x++`
 : 증가 연산자는 수를 증가시키고 증가하기 전 값을 반환합니다.

```javascript
let x = 3;
const y = x++;

// x = 4
// y = 3
```

> ##### 전위연산자 `++x`
 : 증가 연산자는 수를 증가시키고 증가 후 값을 반환합니다. 전위 연산자를 더 많이 사용하지만 크게 의미는 없다

```javascript
let x = 3;
const y = ++x;

// x = 4
// y = 4
```

<br>

### 4. 비교 연산자

``` javascript
let a = 3;
let b = 4;
let c = '4';
let d = 3;

console.log (a > b) //false
console.log (a >= d) //true
console.log (b == c) //true
console.log (b === c) //false

console.clear()

console.log (!0) //true (부정 (반대값 출력))
console.log (a != b) //true
console.log (b !== c) //true
```

> ##### 비교 연산자

1. `a > b` : a가 b보다 크다.
1. `a < b` : a가 b보다 작다.
1. `a >= b` : a가 b보다 크거나 같다.
1. `a <= b` : a가 b보다 작거나 같다.

<br>

> ##### 동등 비교 및 동일성 `=`, `==`, `===`

1. `a = b` : a는 b다
1. `a == b` : a와 b는 같다. (항등 연산자)
1. `a === b` : a와 b는 {% include elements/highlight.html text="타입 까지"%}같다. (완전 항등 연산자)

<br>

> ##### 부정 `!`, `!=`, `!===`

결과 값들을 boolean 값으로만 출력함

1. `!` : =의 반댓값
1. `!=` : ==의 반댓값
1. `!==` : ===의 반댓값


### 5. 논리 연산자

> ##### 논리형 연산자

true와 false 로 값을 반환해주며, and 조건문과 or조건문으로 나눌 수 있다.
1. `&&`(and조건문) : 두가지 조건이 **모두** 만족할 때 `true` 
1. `||`(or 조건문) : **둘 중 하나**의 조건이 만족해도 `true` 

```javascript
let a = 10 > 5; //true
let b = 10 < 5;//false
let c = 5 =='5'; //true

console.log(a && b) //a와 b가 같은 조건인지 -> false
console.log(a || b) //a와 b 둘 중에 하나만 조건을 만족하는지 ->true
console.log(a && c) //a와 c가 같은 조건인지 -> true
```

> ##### 삼항 연산자

조건문 ? true일 때 출력 : false일 때 출력<br>
if...else문의 대체재로 빈번히 사용된다고 한다.

```javascript
let e = 10;
let f = 20;

let result = e < f ? '맞아요' : '틀려요';
console.log(result) //결과 : 맞아요
```






