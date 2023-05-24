## SEB_TIL

## HTTP/네트워크 기초
- 쇼핑몰 앱처럼 실시간으로 팔고있는 물건이 변경되거나, 가격이 변동되는 경우에 서버의연결없이 작동하는 프로그램은 해당 변경내용을 수시로 업데이트 해줘야 하는 번거로움이 생긴다.
- 서버를 두고 실시간으로 변하는 내용을 불러와서 클라이언트에 해당 변경점만 적용된 부분만 변경해주면 번거로운 업데이트 없이 사용자경험을 개선시킬 수 있다.
- 클라이언트와 서버간의 약속된 통신규약을 담아놓은 API(Apllication Programming Interface)를 통해 통신가능.


## URL 과 URI
- URL : Uniform Resource Locator의 줄임말로 네트워크상의 웹페이지,이미지,동영상등의 파일이 위치한 정보를 나타낸다.(scheme, hosts, url-path)
- URI : Uniform Resource Identifier 의 줄임말로 일반적인 URL에 query,fragment와 같은 추가요소를 포함한다.
- 127.0.0.1은 로컬 pc 주소이다.
- port는 서버로 진입하는 통로이름이다.


## IP 
- Internet Protocol의 줄임말로 인터넷상에서 사용하는 주소체계를 의미.
- IPv4 : 127.0.0.1 과같이 네덩어리의 숫자들로 이루어진 주소
- IPv6 : IPv4의 주소갯수 한계때문에 2^128개의 주소를 표현할수있는 새로운 주소

## DNS
- 도메인 주소

## HTTP Messages
- 요청과 응답
- 1.start line  2.HTTP headers  3.empty line  4.body
- Stateless(무상태성) 클라이언트와 서버가 통신하는 과정에서 HTTP가 클라이언트나 서버의 상태를 확인하지 않음.

## HTTP Request
- start line : 세가지요소(수행할작업, 요청대상, http버전)작성
- Header : General headers, Request headers, Representation headers
- body : single-resource bodies , Multiple-resource bodies

## HTTP Response
- status line : 응답의 첫줄로서 현재 프로토콜버전, 상태코드, 상태 텍스트를 포함.
- headers : General headers, Response headers, Representation headers 
- body : single-resource bodies, multiple-resource bodies

## AJAX 
- Asynchronous JavaScript And XMLHttpRequest 의 약자로 자바스크립트,돔,패치와같은 기술을 사용하는 웹개발기법이다.
- 웹페이지의 필요한 부분만 비동기적으로 데이터를 받아와 화면에 그릴 수 있다.
- 서버에서 html을 완성하여 보내주지 않아도 웹페이지를 만들수 있다.
- XHR이 표준화 되면서 브라우저 관계없이 사용가능 
- 유저중심의 애플리케이션 개발가능
- 대역폭의 효율적인 사용가능

## SSR,CSR
- SSR : Server Side Rendering 의 약자로 웹페이지를 브라우저가 아닌 서버에서 렌더링을 진행.
- CSR : Client Side Rendering 의 약자로 클라이언트에서 페이지 렌더링.
- SSR 은 검색엔진 최적화, CSR은 한페이지에서 다양한 상호작용에 유리하다.