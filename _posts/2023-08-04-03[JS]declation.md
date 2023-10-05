---
title: JS 함수 선언 방식
tags: [javascript, function, 함수, 기본개념]
style: fill
color: info
description: 자바스크립트 함수 선언 방식
toc: true
toc_sticky: true
date: 2023-08-04
last_modified_at: 2023-08-04
published: true
---

## 함수 선언 방식

<br>
   
### 1️⃣ 함수 선언문

        function name(){
          실행코드
        };

> ##### 가장 기본적인 방식

```javascript
function sum(a, b){
    return a + b
}
console.log(sum(1,2));
```
결과 : 3

<br>


### 2️⃣ 함수 표현식

        const name = function(){
          실행코드
        };

> ##### 선언은 const로 한다.

```javascript
const sum1 = function(a,b){
    return a * b;
}
console.log(sum1(5, 3));
```
결과 : 15<br>
함수 표현식은 변수명으로만 호출해야하며, 함수에 넣은 이름은 넣어도 되지만 함수 표현식에서는 아무 기능을 하지않음 (호출시 에러)


<br>


### 3️⃣ 생성자 함수

        const Name = new function(){
          실행코드
        };

> ##### 선언은 const로 한다.

```javascript
const User = new function(){
    this.name = 'ME'; //this는 생성자를 뜻한다.
    this.age = '28';
}
console.log(User);
```
결과 : {name: 'ME', age: '28'}
<br>

생성자 함수는 일반 함수와 생성자 함수를 구별하기 위해서 생성자 함수는 **대문자**로 시작하는게 관례이다.

<br>

### 4️⃣ 화살표 함수

> ##### es6부터 새로생긴 함수 선언 방식

```javascript
function = () => {
          실행코드
        };
```


<br>


### 5️⃣ 즉시 실행 함수

        (function(){
          실행코드
        })();

> ##### 함수를 정의하자마자 바로 호출하는 것, 이런 방식에는 이름을 거의 넣지 않는다.(익명 즉시 실행)

함수 표현(Function expression)은 함수를 정의하고, 변수에 함수를 저장하고 실행하는 과정을 거친다.<br>
하지만 즉시 실행 함수는 함수를 정의하고 바로 실행하여 이러한 과정을 거치지 않는 특징이 있다.

<br>

- ##### 이름이 **있는** 경우 : **기명** 즉시 실행 함수

```javascript
(function items(){
    let a = 1;
    let b = 5;
    return console.log(a * b);
}());
```
결과 : 5
<br>
즉시실행 함수이기 때문에 함수명을 호출하면 에러가 뜬다!


<br>

- ##### 이름이 **없는** 경우 : **익명** 즉시 실행 함수

```javascript
(function (){
    let a = 5;
    let b = 10;
    return console.log(a * b);
}());
```
결과 : 50

<br>

- ##### 변수에 즉시 실행 함수 저장

```javascript
(num = function (a) {
    console.log(a * a);
})(2);
num(3);
```
결과 : 4, 9
<br>
함수를 num에 저장하고 이 함수를 바로 실행하게 된다. num은 즉시 실행 함수를 저장하고 있기 때문에 재호출이 가능하다.

<br>

- ##### 변수에 즉시 실행 함수의 리턴 값 저장

```javascript
var num2 = (function (b) {
    return b * b;
})(2);
console.log(num2)
```
결과 : 4

<br>

###### 위의 두가지는 형태가 유사하지만 엄연히 다른 기능이다. 괄호 위치에 주의가 필요!!




