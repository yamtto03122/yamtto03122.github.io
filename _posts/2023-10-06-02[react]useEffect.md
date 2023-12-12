---
title: useEffect
tags: [react, basic, hook]
style: strok
color: primary
description: React Hooks - useEffect
toc: true
toc_sticky: true
date: 2023-10-06
last_modified_at: 2023-10-06
published: true
---
<br>


### useEffect

> ##### : 컴포넌트가 리랜더링 될 때 마다 특정 작업을 실행할 수 있도록 하는 Hook

컴포넌트가 처음 나타났을 때 (mount), 사라질때(unmount), 업데이트(update)가 돼서 리랜더링이 될 때 (props로 값이 바뀔 때)를 말한다.

즉, 클래스형 컴포넌트에서 사용할 수 있었던 생명주기 메소드를 함수형 컴포넌트에서도 사용할 수 있게된것이다.


<br>

#### 1️⃣ useEffect의 형태

``` jsx

useEffect(()=>{
        실행함수
    }, 특정 배열값)

```

<b style="color:#007bff;"> useEffect의 구동방식</b>

- 특정한 값이 변경이 되면 배열의 값을 담아서 <u>변경</u>해주는 방식
- 배열에 특정 값(변경할 값)을 넣게되면 <u>그 값이 변결될 때에만 작동</u>
- 빈 배열을 넣게되면 최초 마운트 시에만 작동
- 기본값은 모든 조건에서 실행


<img src="https://github.com/yamtto03122/yamtto03122.github.io/assets/134922108/794e139c-3b93-4970-80ad-a95c034c84ac" style= "width:100%; margin:1em 0;">
[출처 : CLICK](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)


<br><br>

#### 2️⃣ 사용방법
<br>
<b style="color:#007bff;">기본 형태 : useEffect(function, deps)</b>

- `function` : 수행하고자 하는 작업<br>
- `deps` : 배열 형태이며, 배열 안에는 검사하고자 하는 특정 값 or 빈 배열

<br>

<b style="color:#007bff;">deps에 특정 값 넣기</b>

- deps에 특정 값을 넣게 된다면 컴포넌트가 처음 마운트 될 때, 지정한 값이 바뀔 때, 언마운트 될 때, 값이 바뀌기 직전에 모두 호출이 된다.

- useEffect 안에서 사용하는 상태나, props가 있다면, useEffect의 deps에 넣어줘야하는것이 규칙.

- 만약 사용하는 값을 넣어주지 않는다면, useEffect 안의 함수가 실행 될 때 최신상태, props를 가리키지 않는다.

- deps 파라미터를 생략한다면, 컴포넌트가 리랜더링 될 때 마다 useEffect 함수가 호출된다.

<br>

##### <b style="color:#007bff;"> 1. 컴포넌트가 마운트 됐을 때 실행시키기 (처음 나타났을 때)</b>


> 컴포넌트가 화면에 가장 처음 렌더링 될 때 <b>한 번만 실행</b>하고 싶다면, `deps` 부분에 빈 배열`[]`을 넣는다.

```jsx
import React, { useEffect } from "react";

useEffect(()=> {
    console.log('마운트 될 때만 실행')
},[])

export default Effect;
```

<br>

> 컴포넌트가 <b>리 렌더링 될 때 마다 실행</b>하고 싶다면, `deps` 부분에 배열을 <u>생략</u>한다.

```jsx
import React, { useEffect } from "react";

useEffect(()=> {
    console.log('리랜더링 될 때 마다 실행')
})

export default Effect;
```

<br>


##### <b style="color:#007bff;"> 2. 컴포넌트가 업데이트 됐을 때 실행시키기 (특정 props, state가 변경됐을 때)</b>

> 특정 값이 업데이트 될 때 실행하고 싶을 때에는 deps 위치의 배열 안에 검사하고 싶은 값을 넣어준다.

```jsx
import React, { useEffect } from "react";

useEffect(()=> {

    console.log('hello');
    console.log('업데이트 될 때 마다 실행');

},[name]);

export default Effect;
```
업데이트 될 때에만 실행하는 것이 아니라 마운트 될 때에도 실행된다. 

<br>

> 업데이트 될 때에만 특정 함수를 실행하고 싶다면 ?

```jsx
import React, { useEffect } from "react";

const mount = useRef(false);

useEffect(()=> {

    if(!mount.current){
        mount.current = true;
    } else {
        원하는 코드
    };

},[바뀌는 값]);

export default Effect;
```

컴포넌트가 마운트 될 때에는, if문에서 아무것도 실행하지 않고 mount값만 바꿔주고,

else 에서 배열 안에 있는 값이 바뀌면 원하는 코드를 실행할 수 있다.

<br>


##### <b style="color:#007bff;"> 3. 컴포넌트가 사라질 때(unmount) & 업데이트 직전에 실행시키기</b>

> <u>cleanup함수 반환</u> (return뒤에 나오는 함수이며 UseEffect에 대한 뒷정리 함수라고 한다!)

```jsx
import React, { useEffect } from "react";

useEffect(()=> {

    console.log('hello');
    console.log('name');

    return () => {
        console.log('cleanup');
        console.log(name);
    };

},[]);

export default Effect;
```

1. 컴포넌트가 사라질 때만 cleanup함수를 실행하고 싶을 때 :  두번째 파마리터로 빈 배열을 넣는다.
2. 특정값이 업데이크 되기 직전에 cleanup함수를 실행하고 싶을 때 : deps배열 안에 검사하고 싶은 값을 넣어준다.

<br>


<br><br>

#### 3️⃣ 연습하기

<br>

##### <b style="color:#007bff;">[ 1. p값만 업데이트 되는 버튼 (콘솔x) ]</b> 

<br>

* 로직 : 버튼을 누르면 결과값의 *2 

1. useState로 초기값 설정 : 초기값 설정(2),  세터함수(setMessage) 선언 

2. button 클릭 시 onClick 이벤트에 실행할 내용 부여 (setNum에 변화값 주기) 

3. 콘솔에는 한개의 값만 찍힐 것                                         

<br>

```jsx
import React, { useEffect, useState } from "react";

function Effect(){
   
    const [num, setNum] = useState(2);

    const onClick = () =>{
        setNum(num * 2);
    }
    useEffect(()=>{
        console.log(num)
    },[])

    return(
        <div>
            <p>{num}</p>
            <button onClick={onClick}>CLICK!</button>
        </div>
    )
}

export default Effect;
```

<br>

##### 🔍 결과
<img src="https://github.com/yamtto03122/yamtto03122.github.io/assets/134922108/e41dbc6c-7562-4bc6-a691-9990f24dc24e" style= "height:400px; margin:1em 0;">


`useEffect`의 `deps`를 빈 배열 `[]`로 하면, 콘솔 로그 값에는 num의 기본값이 바뀌지 않고

도큐멘트 상에서의 p 값만 바뀌는걸 확인할 수 있다.

<br><br>

##### <b style="color:#007bff;">[ 2. 카운트다운 만들기 ]</b> 

<br>

* 로직

1. useState에 초기 시간을 설정하고 useEffect로 시간을 차감(setInterval)

2. 0이 되면 카운트(setInterval)가 멈추도록 설정                             

<br>

```jsx
import React, { useEffect, useState } from 'react';

function UseEffect() {
    const [sec, setSec] = useState(10); //카운트다운될 숫자 초기값 설정

    useEffect(()=>{
        const countDown = () => { //변수를 만들어서 setInterval에 대입
            if(sec > 0){ //만약 sec > 0 이라면
                setSec(sec-1); //setSec값에 sec-1값을 대입해줘라
            }else if(sec == 0){ //또는, sec가 0이 되면
                setSec('성공!'); //setSec값에 문자열 '성공!'을 대입해라.
            }
        }

        const timer = setInterval(countDown, 1000); //1초마다 카운트다운을 돌려줌

        return ()=>{
            clearInterval(timer);
        }
    },[sec]); //sec의 값이 바뀔 때 마다 바뀌도록 useEffect 설정

    return (
        <div>
            <p>{sec}</p>     
        </div>
    );
}

export default UseEffect;
```

<br>


##### 🔍 결과

<img src="https://github.com/yamtto03122/yamtto03122.github.io/assets/134922108/8c717dba-9db9-4257-ba71-70ca480b98ec" style= "height:300px; margin:1em 0;">


<br><br>
