# React의 원리

## Vritual DOM이란 무엇인가?

DOM을 조작하는 것은 인터랙티브한 모던 웹의 핵심이지만 자바스크립트의 동작보다 속도가 느리다. 예를 들어 10가지 아이템 중에 하나만 변경되더라도 대부분의 자바스크립트 프레임워크는 전체 아이템을 다시 빌드하게 된다. 즉, 불필요하고 비효율적인 업데이트가 DOM을 조작할 때마다 발생하는 것이다. 이런 문제를 다루기 위해 React는 `virtual DOM`이라고 불리는 것을 고안했다.

React에서 모든 DOM 객체에 대해 상응하는 `virtual DOM object`가 존재한다. `virtual DOM object`란, DOM 객체의 가벼운 복사본과 같은 하나의 표현식으로 실제 DOM 객체와 동일한 프로퍼티들을 가지고 있다. 그러나 화면에 보이는 것들을 직접 바꾸는 힘은 부족하다. DOM을 조작하는 것은 시간이 많이 걸리지만, Virtual DOM을 조작하는 것은 화면에 아무것도 보이지 않기 떄문에 훨씬 빠르다.

JSX element를 렌더링할 때, 모든 virtual DOM 객체가 업데이트 된다. DOM을 조작하는 것과 다르게 Virtual DOM은 매우 빠르게 업데이트되기 때문에 비용적인 면에서 굉장히 효율적이다. **한번 Virtual DOM이 업데이트되면 React는 업데이트 직전에 생성된 Virtual DOM 스냅샷과 현재의 Virtual DOM을 비교하여 정확히 어떤 객체가 변경되었는지 파악하는 과정을 거친다. 이 과정을 `diffing`이라고 한다.** 변경된 Virtual DOM 객체를 알게 되면 React는 실제 DOM에서 해당 객체만 업데이트하게끔 처리한다.

### 요약
1. 전체 가상 DOM이 업데이트된다.
2. 가상 DOM은 어떤 부분이 변경된 것인지 비교하여 변경된 객체를 찾아낸다.
3. 변경된 객체에 한해서만 실제 DOM을 업데이트한다.

## React Component Lifecycle

![](https://i.imgur.com/LHh2JQE.png)

React는 `class component`, `functional component`가 있다. 일반적으로 표현의 목적으로는 function, 컨테이너의 요소로는 class를 사용한다.

### Functional Components

- state가 없고 props를 조작한다.
- Class Component에서 사용하는 라이프사이클 메소드나 setState를 사용할 수 없다.

### Class Components

#### Mounting

특정 컴포넌트의 인스턴스가 생성되고 DOM에 삽입되는 것을 **마운트된다**고 표현한다.

1. constructor()
    - 상속한 컴포넌트의 생성자를 구현할 때는 `super(props)` 호출
    - 생성자 내부에서는 `setState()`를 호출하면 안 됨
    - 반드시 state를 props에 복사하지 않음! -> 버그 발생
2. static getDerivedStateFromProps()
3. render()
4. componentDidMount()
    - 외부에서 데이터를 불러올 때 네트워크 요청을 보내기 적절한 위치

#### Updating

컴포넌트에 전달된 props나 state가 변경되었을 때 컴포넌트는 리렌더되는 단계를 `updating phase`라 한다.

1. static getDerivedStateFromProps()
2. shouldComponentUpdate()
3. render()
4. getSnapshotBeforeUpdate()
5. componentDidUpdate()
    - 최초 렌더링 될 때는 호출되지 않는 메소드
    - 조건문으로 감싸지 않고 `setState()`를 사용하면 무한 렌더링이 발생할 수 있음

#### Unmounting

컴포넌트가 DOM 상에서 제거될 때 호출된다.

1. componentWillUnmount()

#### Error Handling

자식 컴포넌트를 렌더링하거나 자식 컴포넌트가 라이프사이클 메소드를 호출하거나, 자식 컴포넌트가 생성자 메소드를 호출하는 과정에서 오류가 발생했을 때 호출된다.

1. static getDerivedStateFromError()
2. componentDidCatch()

---

### 참고자료
- [React: The Virtual DOM](https://www.codecademy.com/articles/react-virtual-dom)
- [React Component Lifecycle: What Do You Need To Know [2021]](https://www.upgrad.com/blog/react-component-lifecycle/)
- [React Document : react-component](https://ko.reactjs.org/docs/react-component.html)
- [React Lifecycle Diagram](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)