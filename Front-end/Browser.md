# 브라우저의 동작 원리

## 브라우저란?
브라우저는 HTML과 CSS 명세에 따라 HTML 파일을 해석해서 나타낸다. W3C(World Wide Web Consortium) 기준에 기반한다.
과거에는 브라우저에 따른 호환성 문제를 있었으나 최근에는 대부분의 브라우저가 표준 명세를 따른다.

브라우저의 사용자 인터페이스는 다음과 같은 공통적인 요소들을 갖고 있다.
- `URI`를 입력할 수 있는 주소 표시 줄
- 이전 버튼과 다음 버튼
- 북마크
- 새로 고침 버튼, 정지 버튼, 홈 버튼

## 브라우저 렌더링 엔진
HTML 문서 파싱 ▶️ 태그를 DOM 노드로 변환 ▶️ 스타일 요소 파싱 ▶️ 렌더 트리 생성 <br>

더 나은 UX를 위해 가능하면 빠르게 내용을 표시하는데 모든 HTML을 파싱할 때까지 기다리지 않고 배치와 그리기를 시작한다.<br>
네트워크로부터 나머지 내용이 전송되기를 기다리는 동시에 __받은 내용의 일부를 먼저__ 화면에 표시하는 것이다.

> 파싱(parsing) : 브라우저가 코드를 이해하고 사용할 수 있는 구조로 변환하는 것을 의미

엔진 | 설명 | 브라우저
--- | --- | ---
Gecko | 모질라에서 만든 오픈소스 엔진, 렌더 트리를 프레임 트리라고 부름 | 파이어폭스
Webkit | 애플이 개발한 오픈소스 엔진, HTML과 Body 태그를 처리 후 렌더트리 생성 | 사파리, 크롬 
Presto | 오페라 소프트웨어가 개발한 엔진, 렌더링 속도는 가장 빠르지만 호환성이 안좋음 | 오페라

## 동작 원리

### 1. DOM 트리 생성 `WHAT`

- HTML 마크업을 처리하고 DOM 트리를 빌드한다.
- HTML은 부분별로 실행될 수 있다.
- 페이지를 추가하기 위해서 전체 문서가 로드될 필요는 없다.

### 2. CSSOM 트리 생성 `HOW`

- 문서의 스타일과 관련된 CSS Object Model을 생성한다.
- render blocking resource : 리소스가 전부 파싱되지 않으면 렌더트리를 생성할 수 없음
- HTML과 다르게 CSS는 부분별로 사용될 수 없다.
- JS 파일은 CSSOM이 생성될 때까지 대기해야 한다.

### 3. 자바스크립트 실행

- parser blocking resource : JS에 의해 HTML 도큐먼트 파싱이 block된다.
- 파서가 `<srcipt>` 태그를 만나면 fetch하는 것을 중단하고 JS 파일을 기다린다.
- `<srcipt>` 태그를 HTML 문서 하단에 위치시키는 이유
- 비동기적으로 스크립트를 가져오려면 `async` attribute를 추가한다.

### 4. 렌더 트리 생성 `DISPLAY`

- DOM 및 CSSOM 을 결합한 것이 렌더 트리가 된다.
- 이때 포함되는 것은 visible content가 된다. `display : none`이라면 포함되지 않는다.

### 5. 레이아웃 생성

- 렌더링 트리에서 레이아웃을 실행하여 각 노드가 정확한 위치에 표시되도록 배치한다.

### 6. 페인팅

- visible content가 스크린에서 픽셀단위로 display된다. 
- 배치된 노드를 스타일 속성에 맞게 그린다.

### 참고
- [Naver D2](https://d2.naver.com/helloworld/59361)
- [Understanding the Critical Rendering Path](https://bitsofco.de/understanding-the-critical-rendering-path/)