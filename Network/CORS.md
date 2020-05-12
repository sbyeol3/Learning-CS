# CORS(Cross-origin resource sharing), 교차 출처 리소스 공유
추가적인 HTTP 헤더를 이용하여 자신의 출처(도메인, 프로토콜, 포트번호)와 다른 출처의 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제를 의미한다.
`XMLHttpRequest`나 `Fetch API`, `Ajax` 등을 사용하여 다른 도메인의 자원을 요청하는 경우 브라우저는 이 요청을 `SOP`에 의해 제한한다.
리소스를 요청하기 위해서는 요청을 받는 대상과 프로토콜, 포트번호도 같아야 한다는 것이다. 서브 도메인 네임은 같지 않아도 된다.<br>
즉, 자신의 출처와 동일한 리소스만 요청할 수 있고 다른 출처의 리소스를 요청하려면 해당 출처에서 CORS 헤더를 포함한 응답을 반환해야 한다.
CORS 표준은 웹 브라우저가 출처 집합을 서버에게 알려주는 추가적인 HTTP 헤더를 보내 동작한다.

## Preflight Request
요청하려는 대상이 외부의 도메인이라면 preflight request를 먼저 날려야 한다. 요청을 미리 날려서 요청 권한이 있는지 확인한다.

### 서버에서 request handling
모든 요청의 응답에 아래 표와 같이 헤더를 추가한다.

key | value
--- | ---
Access-Control-Allow-Origin | *
Access-Control-Allow-Methods | GET, POST, PUT, DELETE, OPTIONS
Access-Control-Max-Age | 3600
Access-Control-Allow-Headers | Origin,Accet,X-Requested-With, Content-Type, Access-Control-Request-Method, Access-Control-Request-Headers,Authorization

<br>

## SOP(same-origin policy), 동일 출처 정책
어떤 출처에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는 것을 제한하는 웹 보안 모델
잠재적으로 해로울 수 있는 문서를 분리함으로써 가능한 공격 경로를 줄이는데 도움을 줌

JavaScript는 스크립트를 포함하고 있는 문서와 같은 출처의 문서에 있는 window와 Document 객체의 속성만을 사용할 수 있다. 
스크립트 파일의 출처는 동일 출처 정책과 전혀 관계가 없고 중요한 것은 스크립트를 포함하고 있는 문서의 출처다. 


---
### 참고
[MDN web docs](https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy)<br>
[양은냄비님의 기술브로그](https://iamawebdeveloper.tistory.com/38)