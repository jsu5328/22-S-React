# 4-week-soyun-1

<aside>
💡 7강 1,2듣기 / useState, useEffect, useRef 조사

</aside>

- Self Closing
    
    `<태그 />` 
    
    태그와 태그 사이에 아무 내용이 들어가지 않을 때, `<태그 />` 로 해줄 수 있습니다.
    
- 리액트 Fragment
    
    두 개 이상의 태그를 넣을 때, 꼭 하나의 태그로 닫아줘야한다.
    
    div태그로 묶기 좀 불편하면 `<> </>`로 묶어도 된다. `<> </>`가 바로 Fragment이다.
    
    ```jsx
    function App(){
    	return(
    		<>
    			<div/>
    			<div/>
    		</>
    	);
    }
    ```
    
- 리액트 주석
    
    `{/* */}`
    

# useState

state(상태)란, 컴포넌트에서 동적인 값을 의미한다.

state를 관리하기 위해, `useState` 라는 함수를 사용한다.

```jsx
/*useState를 사용하기 위해 import해야할 것*/
import React,{useState} from'react';

/*사용하기(배열 비구조화 할당)*/
const [number,setNumber]=useState(0);
```

```jsx
import React from 'react';

function Counter() {
  const onIncrease = () => {
    console.log('+1')
  }
  const onDecrease = () => {
    console.log('-1');
  }
  return (
    <div>
      <h1>0</h1>
      <button onClick={onIncrease}>+1</button>
      <button onClick={onDecrease}>-1</button>
    </div>
  );
}

export default Counter;
```

```jsx
import React from 'react';
import Counter from './Counter';

function App() {
  return (
    <Counter />
  );
}

export default App;
```

- 배열 비구조화 할당
    
    ```jsx
    useState(0);
    const numberState=[useState[0],useState[1]];
    const number=numberState[0];
    const useState=numberState[1];
    
    /*배열 비구조화 할당*/
    const [number,setNumber]=useState(0);
    ```
    
    ![0726-1.png](https://polyester-orchestra-61e.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F4b7a8702-7006-4c0d-a794-348375a3f326%2F0726-1.png?table=block&id=24edee3d-897b-48f9-91a7-4687a0d7a6f1&spaceId=9e9794b7-89ce-4e4b-ad10-420fe112a252&width=1340&userId=&cache=v2)
    

`useState()` 는 배열을 생성해주는 함수이다.

배열의 첫 번째 원소는 ‘현재 상태’

배열의 두 번째 원소는 ‘Setter함수’ 이다. 

```jsx
/* setNumber(파라미터); */
setNumber(number+1);
```

Setter 함수는 전달 받은 값을 최신 상태로 하는 파라미터를 넣어 상태를 설정(set)해준다.

# useEffect

`useEffect()` 함수는 파라미터를 두개 넣는다. 

첫번째 파라미터에는 함수를 넣는다.

이 함수는 의존값이 변함에 따라 재렌더링 되는 코드를 정의한다.

두번째 파라미터에는 의존값이 들어있는 배열(deps)을 넣는다. 

의존값이 변화하면 함수가 재렌더링(재정의)된다.

# useRef

DOM 을 직접 손대지 않고 가상 DOM을 수정하여 DOM에 변화를 주는게 리액트지만, DOM을 선택해야 할 때가 있다.

이때 쓰는게 `useRef()` 함수이다.

+) 컴포넌트 안에서 조회 및 수정할 수 있는 변수를 관리할 때도 사용한다고함.

useRef 로 관리하는 변수는 변경사항이 생겨도 컴포넌트가 리렌더링 되지 않는다.