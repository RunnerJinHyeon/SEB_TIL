# SEB_TIL

## Rest API
- 웹에서 사용되는 데이터나 자원을 http uri로 표현하고 http 프로토콜을 통해 요청ㄹ과 응답을 정의하는방식

### 0단계
- 단순히 http프로토콜 사용. 이경우 rest api라고는 부를수 없으며 rest api를 작성하기 위한 기본단계이다.
- 요청 : POST/appointment HTTP/1.1
- 응답 : HTTP/1.1 200 OK

### 1단계
- 개별리소스의 통신을 준수해야한다.
- 요청 : POST/(개별리소스에 맞는 엔드포인트) 사용 HTTP/1.1
- 응답 : HTTP/1.1 200 OK

### 2단계
- CRUD(create, read, update,delete)에 맞춰작성
- Read : GET 메소드와 query parameter를 사용하여 필요한 리소스 전달
- Create : POST 메소들르 사용하여 요청, 응답은 201 Created 처럼 명확하게 작성.
- PUT은 교체,PATCH는 수정

### 3단계
- 요청은 2단계와 같으나 응답에 리소스의 URI를 포함한 링크요소를 포함해야한다.
- HATEOAS(Hypermedia As The Engine Of Application State)
