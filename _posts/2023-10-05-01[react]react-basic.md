---
title: jsx 문법
tags: [react, basic, jsx]
style: fill
color: primary
description: 리액트 기초 중의 기초 시작..!
toc: true
toc_sticky: true
date: 2023-10-05
last_modified_at: 2023-10-05
published: true
---

## jsx(javascript XML) 문법

> ##### 확장형 자바스크립트 문법으로 html과 비슷한 문법

일반 스크립트 문법은 아니기 때문에, 브라우저에서 실행되기 전에<br>
코드가 번들링 되는 과정에서 **바벨**을 사용하여 일반 자바스크립트 형태의 코드로 변환된다.

예를 들어,

```jsx

function App(){
	return (
    	<div>
        	Hello <b>react</b>
        </div>
    );
}

```

위의 코드는 아래 형태의 코드로 변환된다는 말이다.

  ```jsx
  function App(){
    return React.createElement("div", null, "Hello", React.createElement("b", null "react"));
  }

  ```

  <br>

## jsx문법 작성 규칙
  
### 1️⃣ 부모태그

> ##### 여러 개의 요소를 사용할 때에는 반드시 부모태그로 감싸줘야한다.

**하나의 부모태그로 감싸줘야 하는 이유!**<br>

virtual DOM에서 컴포넌트 변화를 감지내 낼 때, 효율적으로 비교할 수 있도록 컴포넌트 내부는 하나의 DOM트리 구조로 이루어져야 한다는 규칙이 있다.

보통 `<div>`로 감싸지만 `<>`~`</>`와 같은 빈 태그`<fragment>`로 감쌀 수도 있다.

```jsx
import React from 'react';

// 잘못된 코드
function App(){
  return(
      <h1>Hello</h1>
      <h2>Is it working well?</h2>
    )
}

// 올바른 코드
function App(){
  return(
      <div>
        <h1>Hello</h1>
        <h2>Is it working well?</h2>
      </div>
    )
}

export default App;
```

<br>

### 2️⃣ 자바스크립트 표현식

> ##### jsx 내부에서 코드를 `{}`로 감싸면 javascrip표현식을 작성할 수 있다.

```jsx
import React from 'react';

function App(){
  const name = 'react';
    return(
      <>
        <h1>Hello! {name}</h1>
        <h2>Is it working well?</h2>
      <>
    )
}
export default App;
```

<br>


### 3️⃣ if문 대신 삼항 연산자

> ##### jsx 내부의 자바스크립트 표현식에서는 if문을 사용할 수 없다.

하지만! 조건에 따라 다른 내용을 출력하고싶다면 jsx문 밖에서 if문을 사용하여 미리 값을 설정해놓거나, `{}`안에 삼항연산자 (조건부 연산자)를 사용하면 된다! 

여기서 삼항연산자를 다시 떠올려본다면?! `A ? B:C` A라는 조건이 맞으면 B가 실행, 아니라면 C가 실행되는 조건문이었다!!

```jsx
import React from 'react';

function App(){
  const name = 'react';
    return(
      <div>
        {name === 'react'? (<h1>This is react</h1>) : (<h2>This isn't react</h2>)}
      </div>
    )
}

export default App;
```

<br>

### 4️⃣ class 대신 classname을 사용

```jsx
import React from 'react';

function App(){
  const name = 'react';
    return(
      <div>
        <div className="item">item</div>
      </div>
    )
}

export default App;
```

<br>

### 5️⃣ 싱글태그도 무조건 닫혀있어야 한다.

> ##### `<img/>`와 같은 싱글태그도 `/>`를 사용하여 닫아줘야한다.

```jsx
import React from 'react';

function App(){
  const name = 'react';
    return(
      <div>
        <img src=""/>
      </div>
    )
}

export default App;
```

<br>

### 6️⃣ 인라인 스타일 기법

인라인 스타일을 적용 할 때에는 클레스네임을 사용할 수 없고 `{객체형태}`로 전달해야한다.

key값에는 `-`을 사용할 수 없기 때문에 카멜 기법으로 사용해야한다. ex) font-size -> fontSize


```jsx
import React from 'react';

function App(){
  const name = 'react';
  const item = {
        background : 'yellow',
        fontSize : '21px'
    }
    return(
      <div>
        <div className="item">item</div>
      </div>
    )
}

export default App;
```

<br>

### 7️⃣ and 연산자를 사용한 조건부 랜더링

특정 조건을 만족할 때는 출력하지 않고, 만족하지 않을 때에는 출력하지 않아야 하는 상황이 올 때가 있다.

삼항연산자로도 구현할 수 있지만 and(&&)연산자를 사용하면 똑같은 코드도 더 짧은 코드로 작업을 할 수가 있다. 


```jsx
import React from 'react';

// AND 연산자
function App(){
  const name = 'rreact';
    return(
      <div>
        {name === 'react' && <h1>It's correct</h1>}
      </div>
    )
}

export default App;
```

위 코드의 결과로는 브라우저에 아무것도 나타나지 않는다.

`&&` 연산자로 조건부 랜더링을 할 수 있는 이유는 리액트에서 false를 렌더링 할 떄에는 null과 마찬가지로 아무것도 나타나지 않기 때문이다.

여기서 한 가지 주의해야 할 점은! {% include elements/highlight.html text="flasy한 값인 0은 예외적으로 화면에 나타난다는 점!!!"%}

<br>

```jsx
const number = 0;
return number && <div>내용</div>
```

위 코드에서는 '내용'을 보여주지 않고 '0'을 보여준다!
