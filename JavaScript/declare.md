# JavaScript 변수 선언 `var` `let` `const` 차이
JavaScript는 느슨한 타입 (loosely typed) 언어, 혹은 동적 (dynamic) 언어로 변수의 타입을 미리 선언할 필요가 없다. 

## `var`
ES6(ECMAScript 6) 이전에는 변수를 선언하기 위해서는 `var`라는 키워드를 사용했다.<br>
`var`는 함수 블록만 scope로 인정하므로 `(functional-level-scope)` 함수 블록의 외부에서 선언된 변수는 모두 전역변수로 사용된다. 

## `var`의 문제점
같은 이름을 가진 변수가 중복되게 선언될 수 있다.
```javascript
var name = "Yang"
console.log(name) // Yang

var name = "Ahn"
console.log(name) // Ahn
```

```javascript
for(var j=0; j<10; j++) {
  console.log('j', j)
}
console.log('outside', j)
```

javaScript는 모든 선언을 호이스팅한다. 그러나 `let`이나 `const`에 한해서 선언된 변수들은 일시적으로 호이스팅이 되지 않는 사각지대에 빠지기 때문이다.


_`호이스팅(Hoisting)` : 선언문 등을 해당 스코프의 선두로 옮긴 것처럼 동작하는 것._

변수는 선언 단계 > 초기화 단계 > 할당 단계에 걸쳐 생성되나, `var`로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어지므로 변수 호이스팅이 가능하다. 즉, 변수가 선언되기 전에 변수를 참조할 수 있다.

## `let` vs. `const`
__변수의 재할당이 가능한가?__ immutable <br>
가능하다면 `let`, 불가능하다면 `const`

```javascript
let day = "mon"
day = "tue"
day = "wed"
```
위와 같이 코드를 작성해도 에러가 나지 않는다.

```javascript
const day = "mon"
day = "tue"
// Uncaught TypeError:Assignment to constant variable.
```
`const`는 이미 선언된 변수에 값을 재할당할 수 없으므로 에러가 발생한다.

기본적으로는 `const`를 주로 사용하고, 재할당을 해야 하는 경우에만 `let`을 이용한다.

### 참고
> https://developer.mozilla.org/ko/docs/Web/JavaScript/Data_structures <br>
> https://velog.io/@bathingape/JavaScript-var-let-const-%EC%B0%A8%EC%9D%B4%EC%A0%90