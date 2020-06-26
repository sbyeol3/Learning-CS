# null vs. undefined

## JavaScript 자료형
-  Primitive values : immutable
-  Object

__`primitive values`__
- Boolean
- Null
- Undefined
- Number : +/- Infinity, NaN
- String
- Symbol

## Null과 Undeifned란

### Null
자바스크립트에서의 `null`은 다른 프로그래밍 언어에서 사용하는 `null`과 성격이 다르다.
다른 언어에서는 '존재하지 않는 객체에 대한 참조'나 'null pointer'를 나타낼 때 사용한다.
Number로 사용하면 0으로 변환된다.

-> 존재하지 않는 값 `nothing`, 비어 있는 값 `empty`, 알 수 없는 값 `unknown`

```javascript
let name = null;
typeof null; // object지만 객체가 아님
```

### Undefined
값이 할당되지 않은 상태, 해당 변수의 자료형이 정해지지 않은 상태를 의미한다.
null처럼 직접적으로 할당은 할 수 있지만 권장하지 않는다. Number로 사용하면 NaN으로 변환된다.
```javascript
let name;
console.log(name); // undefined
typeof undefined; // undefined
```

```javascript
undefined == null // true
undefined === null // false
```

null과 undefined는 모두 `falsy`한 값이다.

### 참고
> [모던 자바스크립트](https://ko.javascript.info/types)