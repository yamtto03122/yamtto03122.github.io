---
title: hook과 State
tags: [react, basic, hook, state]
style: fill
color: primary
description: hook, state 개념 이해하기
toc: true
toc_sticky: true
date: 2023-10-05
last_modified_at: 2023-10-05
published: true
---
<br>

> ### 1️⃣ hook이란?

리액트는 <b>클래스형</b>과 <b>컴포넌트</b>로 구분한다.<br>
옛날 버전에서는 함수형을 메인으로 사용하면서, 값의 변경이나 라이프 사이클을 사용할 때에는<br>
클래스형 컴포넌트를 구분해서 사용해야 했다.<br>
<u>클래스형 컴포넌트의 단점</u>은 코드가 너무 복잡하고, 한번 만든 로직은 재활용이 불가능하다.

<br>

##### 이러한 단점을 보완해서 만든게 `hook`!!!!

함수형 컴포넌트에 클래스형 컴포넌트의 기능을 사용할 수 있게 해주는 일종의 확장 기능이다.

대표적으로 `useState`, `useEffect`, `useReducer`가 있다.


<br>
  
### 2️⃣ State란?

> ##### 리액트에서 이벤트에 의해 변경되는 동적인 값!

<br>
<u>props의 단점</u>은 컴포넌트 내부에서 값을 변경할 수 없다.<br>
그래서 <b>값을 바꿔야 하는 경우에는 props 대신에 state로 사용</b>한다.<br>
값을 저장하거나 변경해야하는 객체에 주로 사용하며, 이벤트 요소와 함께 사용할 수도 있다.
컴포넌트에서 받아온 값은 state라고 한다.
<br>

1. 버튼을 클릭하는 `onClick` 이벤트, `input` 입력으로 인해 발생하는 `onChange` 이벤트에 의해 <u>입력값이 변경된 경우 사용</u>
2. props는 부모 컴포넌트가 설정하는 값이며 읽기 전용이지만, state는 하위 컴포넌트도 데이터를 변경할 수 있다.
3. 함수형 컴포넌트는 `useState`라는 Hook 을 사용하여 state를 다룰 수 있다.

<br>

### 3️⃣ State 사용
<br>

#### 1. useState

> ##### : 리액트의 기본 Hook 중 하나로, 컴포넌트에서 state를 추가할 때 사용!!

<br>

##### <b style="color:#007bff;">- useState의 형태</b>

``` jsx

const [ state, setState ] = useState(initialState);
const [ 상태, 세터함수 ] = useState(초기값);

```

useState 함수를 호출하면 배열 [state, setState] 이 리턴된다.

배열의 첫번째 요소 : 현재 상태(state)이고,<br>
배열의 두번째 요소 : <b>상태를 바꾸어주는 setState 함수가 리턴</b>

useState 함수 인자에는 상태의 초기값을 넣어주는데, 이건 생략 가능하다! (비워놔도 된다.)

<br>

##### <b style="color:#007bff;">- 사용방법</b>

<u><b>반드시 setState 로 데이터를 변경하기</b></u>

state 값을 변경할 때는 반드시 <b>`setState`</b>를 사용하여 변경해야 한다.<br>
state값이 변경되면 useState가 변경을 감지하고, 자식 컴포넌트들까지 리렌더링이 발생하게 되기 때문이다.<br>
직접 state를 수정하게 되면 리액트가 render 함수를 호출하지 않아 변경이 일어나도 렌더링이 일어나지 않을 수 있다. 주의!

<br>

##### <b style="color:#007bff;">- 연습하기 [ 1. input태그 하나일 경우 ]</b> 

<br>

* 로직 : input값에 따라 변하는 메시지 

1. useState로 message 관리 : 초기값 설정,  세터함수(setMessage) 선언 

2. event 로 발생한 value 값을 Message에 대입해서 state를 갱신하기  

3. 초기화 버튼 누르면 리셋                                         

<br>

```jsx
import React, { useState } from 'react';

function UseState() {

    const [message, setMessage] = useState(''); 

    const onChange = (e) => {
        setMessage(e.target.value);

    }

    const reset = () => { //초기화
        setMessage('');
    }


    return (
        <div>
            <h2>MESSAGE</h2>
            <input onChange={onChange} value={message}/>
            <p>내용 : {message}</p>
            <button onClick={reset}>RESET</button>
        </div>
    );
}

export default UseState;
```

<br>

##### 🔍 결과
<img src="https://github.com/yamtto03122/yamtto03122.github.io/assets/134922108/0a0a576d-a153-4531-b979-6120fe3135a8" style= "height:400px; margin:1em 0;">


input창에 입력한 텍스트가 p태그로 나타나고, RESET버튼을 누르면 p태그와 input value 모두 초기화가 되었다.

<br>

##### <b style="color:#007bff;">- 연습하기 [ 2. input태그가 여러 개일 경우 ]</b> 

<br>

* 로직 : input값에 따라 변하는 메시지 

1. 각 태그에 name값 설정

2. useState 객체형태로 받아오게하기                                 

<br>

```jsx
import React, { useState } from 'react';

function UseState() {

    const reset = () => { //초기화
        setInfo({
            names : '',
            age : '',
            address : ''
        })
    }

    const [info, setInfo] = useState({
        names : '',
        age : '',
        address : ''
    });

    const {names, age, address} = info; //객체를 구조분해할당을 해준 것

    const onChange = (e) => {
        const { value, name } = e.target;
        setInfo({...info, [name] : value});
        console.log(info)
    }

    return (
        <div>
            <div>
                <h2>Introduction</h2>
                <input name="names" placeholder="이름" onChange={onChange} value={names}/>
                <input placeholder='나이' onChange={onChange}  name="age"  value={age}/>
                <input placeholder='거주 지역' onChange={onChange}  name="address"  value={address}/>
                <p>이름 : {names}, 나이 : {age}, 거주지 : {address}</p>
            </div>

            <button onClick={reset}>RESET</button>
        </div>
        
    );
}

export default UseState;
```

<br>


##### 🔍 결과

<img src="https://github.com/yamtto03122/yamtto03122.github.io/assets/134922108/76ec273f-3555-415f-a960-29ee37d64fba" style= "height:400px; margin:1em 0;">


<br>

```jsx 
const onChange = (e) => {
        const { value, name } = e.target;
        setInfo({...info, [name] : value});
        console.log(info)
    }
```

> 리액트에서는 객체를 변경할때 꼭 <u>원본을 복사하고 그 뒤에 변경할 값을 덮어쓰는 방식</u>을 써야하므로<br>
`...(스프레드 문법)`을 통해서 원본 객체인 info를 <b>복사</b>해준 다음에<br>
위에 변수로 선언한 name을 key값으로 넣어준다.

<br>

[대괄호]를 통해서 키값을 적어주는 것은 <u>변수를 선언하고 그 실제값을 불러오기 위해서 사용하는 것이다.</u> 

따라서 `e.target.name`이 키값으로 들어간 것은 `<input name="names">` 이므로, key값으로 "names"가 들어갈 것이다.

즉, {% include elements/highlight.html text="이벤트의 타깃인 input의 안에 있는 name이 무엇인가? 그 name에 들어간 값을 키값으로 사용하라" %}라는 의미이다.

여기서는 name안에 "names"이라는 값이 들어가 있기 때문에 

inputs안에서 "names"이라는 key를 찾고 그것의 value값을 새롭게 들어오는 값으로 변경을 해준다.

<br>
