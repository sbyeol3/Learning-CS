# CRUD `CREATE, READ, UPDATE, DELETE`
대부분의 소프트웨어가 가지는 기본적인 데이터 처리 기능 4가지 `CREATE, READ, UPDATE, DELETE`를 묶어서 일컫는 말, Kilov, H(1990)의 논문에서 최초로 사용됨. 트랜잭션(transaction) 분야에서 사용되는 ACID와는 다른 것이므로 주의해야 함.
<br>


name | operation | SQL | 예시
--- | --- | --- | ---
Create | 생성 | INSERT | 새로운 연락처 추가
Read(Retrieve) | 읽기, 인출 | SELECT | 특정 연락처 조회
Update | 갱신 | UPDATE | 연락처 정보 편집 
Delete(Destroy) | 삭제, 파괴 | DELETE | 특정 연락처 삭제

### CRUD와 REST 차이점
`CRUD`는 데이터 저장소에서 작동되는 기본적인 opration으로 레코드나 데이터를 직접적으로 다룰 수 있다. 대부분 데이터베이스나 정적인 데이터 저장소를 위한 기초적인 기능들의 집합을 의미한다. 반면에 `REST`는 URL로 식별되는 자원에서 작동한다. 웹 서비스와 같은 곳에서 필요한 고차원적인 API 형식을 의미한다.

***
### 참고 자료
>[difference between rest and crud](https://qastack.kr/software/120716/difference-between-rest-and-crud) <br>
> [CRUD 위키백과](https://ko.wikipedia.org/wiki/CRUD)