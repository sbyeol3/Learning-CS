# 정규표현식, 정규식
-> 정규 표현식을 줄여서 정규식이라고 함<br>
텍스트가 준수해야 하는 패턴을 표현하기 위한 특정 표준의 텍스트 문법<br><br>
특정한 규칙을 가진 문자열의 집합을 표현하는 데 사용하는 형식 언어<br>
텍스트 편집기나 프로그래밍 언어에서 문자열의 검색과 치환을 위해 지원

JavaScript 프로그래머에게 반드시 필요한 개념
  
:link [정규식 실습 사이트](https://regex101.com/)

## 정규식 Cheet Sheet
- `^` & `$` <br>
  
example | description 
--- | --- 
^A | A로 시작하는 문자열
Z^ | Z로 끝나는 문자열
^Hello$ | Hello와 일치하는 문자열
World | World가 들어있는 문자열


- `*` & `+` & `?` & `{ }`

example | description 
--- | --- 
ABC* | AB + 0개 이상의 C가 있는 문자열
ABC+ | AB + 1개 이상의 C가 있는 문자열
ABC? | AB 또는 ABC인 문자열 (C가 0개 또는 1개)
ABC{3} | AB + CCC (C가 3개)를 포함한 문자열
ABC{1,5} | AB + 1개 이상 5개 이하의 C를 포함한 문자열
A(BC)* | A + 0개 이상의 BC를 포함한 문자열

- `|` & `[]` : OR 연산자

example | description 
--- | --- 
A(B\|C) | A + (B 또는 C)를 포함한 문자열 = AB~, AC~

- char 타입

example | description 
--- | --- 
\d | 숫자 1개
\w | 문자 1개 (숫자, 영문자, 언더바`_`)
\s | 공백문자 (탭, 줄바꿈, 스페이스) 1개
. | 모든 문자 1개
\대문자 | NOT의 의미로 사용 `ex. \S = 공백문자가 아닌 문자 1개`


<br>

## JavaScript 정규식 생성

- `Constructor method`
```Javascript
const regexp = new RegExp("ABC+");
```

- `Literal` 방식 : `/`로 감싸진 패턴, 따옴표 없음
```Javascript
const regexp = /ABC+/;
```

- 재할당을 하려면 `let`으로 변수 선언해야 함

<br>

## JavaScript 판단

- `exec` & `match` : 일치하는 결과 없으면 null 리턴
```Javascript
const str = 'example yeah meosigi';

// exec 함수
/example/.exec(str);

// match 함수
str.match(/example/);
```
<br>

## Flag
검색하려는 문자 패턴에 추가적인 옵션을 부여하여 검색 결과를 리턴받음
flag | description 
--- | --- 
g(global) | 모든 문자와 여러 줄 일치
i(insensitive) | 영어 대소문자 구분 안함
m(multi line) | 여러 줄 일치
u(unicode) | 유니코드
y | `lastIndex` 속성으로 지정된 인덱스에서만 1회 일치

```Javascript
const str = `Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.`;

str.match(/ipsum/i);
// ["Ipsum", index: 6, input: "Lorem Ipsum is simply dummy text of the printing a…ldus PageMaker including versions of Lorem Ipsum.", groups: undefined]

str.match(/ipsum/ig);
// (4) ["Ipsum", "Ipsum", "Ipsum", "Ipsum"]
```

***
### 참고 자료
>[정규표현식, 이렇게 시작하자!](https://heropy.blog/2018/10/28/regexp/)