# 4-week-soyun-3

```jsx
// Dom의 Event
<button onclick="activate()">
	Activate
</button>

//리액트의 Event
<button onClick={actice}>
	Activate
</button>
```

차이점: 

1. onClick이 카멜케이스로 표기되어있음.
2. Dom는 문자열로 전달하지만, 리액트는 함수 그대로 전달함.

# Event Handler

- Event Listner라고도 함.
- 어떤 사건이 일어나면, 그 사건을 처리하는 역할.

## 클래스 컴포넌트에서 Event Handler을 추가하는 방법

```jsx
{ 
	this.handleClick=this.handleClick.bind(this);
}

hadleClick(){
	this.setState(prevState => 
	({isToggleOn:!prevState.isToggleOn})
	);
}

```

Global scope 에서 this.handleClick은 undefined이기 때문에 bind 해줘야한다.

- 지역변수
    
    [02 보충자료](https://www.notion.so/02-fb7b31feed0e4f63a875f548ee278a25)
    

```jsx
<button onClick= { ()=> this.handleClick() }>
	클릭
</button>
```

이벤트 핸들러를 넣는 곳에 화살표 함수를 사용하면 bind를 안써도 바운드된다.

근데 이렇게 하면 이 핸들러가 들어있는 컴포넌트가 렌더링될 때 마다 다른 콜백함수를 생성하는 문제가 발생한다.

이 콜백함수가 하위 컴포넌트의 prop으로 넘겨지게 되면 하위 컴포넌트에서 추가적인 렌더링이 발생하게 된다.(성능문제)

결론→걍 bind쓰자

## 함수형 컴포넌트에서 Event Handler를 사용하는 방법

방법 1. 함수 안에 함수로 정의

방법 2. 화살표 함수를 사용하여 정의

그리고 함수컴포넌트에서는 이벤트 핸들러를 쓸때this 안쓰고 onClick에 넘겨도 됨.

*argument vs Parameter

Argument: 전달할 데이터

Parameter: 매개변수