# Document Object Model (DOM)

## DOM이란 무엇인가?

- 웹 페이지에 대한 인터페이스, 페이지의 요소를 읽고 조작할 수 있게 하는 프로그램이 가능하게 한다.
- HTML 문서의 내용과 구조가 객체 모델로 변환된다. (Object 기반 표현방식)

## DOM의 구조

- DOM의 개체 구조는 노드 트리로 표현된다.
- `document.documentElement`는 root 역할을 한다.
- `documentElment` 프로퍼티는 `<html>` 태그를 나타내는 오브젝트를 참조한다.
- element에 해당하는 Node들은 HTML 태그로 표현되고 document의 구조를 결정한다.
- 각 노드는 자신의 childe node를 가질 수 있다.
- 각 DOM node Object는 노드의 타입을 결정하는 넘버를 의미하는 `nodeType` 속성을 가지고 있다.

![](https://i.imgur.com/8njOpMb.png)

## DOM 특징

- DOM은 HTML과 동일하지 않다.
- DOM과 렌더트리는 다르다. 렌더트리는 스크린에 그려지는 것으로만 구성되어 있다.


### 참고자료
- [eloquent javascript : DOM](https://eloquentjavascript.net/14_dom.html)
- [What, exactly, is the DOM?](https://bitsofco.de/what-exactly-is-the-dom/?utm_source=CSS-Weekly&utm_campaign=Issue-341&utm_medium=email)