# JavaScript map & forEach 메소드 정리

두 메소드의 공통점은 Array에 관한 메소드이다. (프론트엔드 개발을 하면서 굉장히 자주 쓰는 메소드)
또한 Array의 원소들을 순회하면서 함수를 실행하는 목적으로 사용된다.
  

그러나, `forEach`는 `return value`가 없고 Array의 원소마다 provided된 함수를 한 번씩 실행하는 메소드이다.
`map`은 함수들을 호출한 결과를 모아서 **새로운 Array를 리턴하고** 이때 리턴하는 Array는 반복하는 array와 동일한 길이를 갖는다.
사용하는 배열 자체를 변경하려면 forEach가 더 낫고 새로운 배열을 반환하고 싶을 때는 map을 사용하는 것이 좋다. 
React에서는 불변성을 유지하는 것이 중요해서 상태 관리를 할 때는 map 메소드를 이용해서 원본 배열을 복사하고 데이터를 수정하거나 추가하는 형식으로 사용한다.
  
Array의 원소들이 순차적으로 차 있지 않은 경우 for문을 사용하면 Array의 length만큼 실행하므로 불필요한 연산을 할 수 있다.
예를 들어 A라는 배열에서 인덱스 0과 50에만 데이터가 있고 나머지는 `null`이라면 두 개의 데이터를 위해 for loop는 51번 연산을 해야 한다.
그러나 map이나 forEach는 메소드 내에서 여러 조건을 체크하므로 인덱스 0과 50에서만 실제 연산을 실행하게 되므로 효율적이다.

시간적인 성능은 `forEach > map`라고 한다. map은 결과 값을 새로운 변수에 담아서 리턴하는 작업을 수행해야 하므로 메모리 할당이 필요하다.
시간복잡도는 O(n)으로 동일하기는 하나 map이 할당 등의 추가적으로 수행해야 하는 연산들이 있기 때문에 차이는 발생할 수 있다.

## 예제
```javaScript
// map
const example = [1,2,3,4,5]
const returnArr = example.map((value,index) => {return value*index})
console.log(returnArr)
// -> (5) [0, 2, 6, 12, 20]

// forEach
const example = [1,2,3,4,5]
const returnArr1 = example.forEach((value,index) => {return value*index})
console.log(returnArr1)
// -> undefined
```


### 참고
[Javascript-map()과 forEach()의 비교 및 분석](https://pewww.tistory.com/12)<br>
[JS - Map vs ForEach](https://frontdev.tistory.com/entry/JS-Map-vs-ForEach)