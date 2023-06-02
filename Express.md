## SEB_TIL

## Express
- npm install express 로 시작.
- const app = express() 선언으로 get,listen과 같은 메소드 활용가능(ex: app.get('/',(req,res)=>{
    res.send("hello")
})
- Express는 프레임워크 자체로 라우터기능을 내장하고 있기 때문에 위와같은 get,post같은 라우팅메소드 사용이 가능하다.

## 미들웨어
- 요청에 필요한 기능을 더하거나 문제가 발견된 요청을 걷어내는 역할.


## 미들웨어 사용상황
- POST 요청등에 포함된 body(payload)를 구조화 할때.
- 모든 요청/응답 에 cors헤더를 붙여야 할때.
- 모든요청에 대해 url이나 메소드를 확인할때.
- 요청 헤더에 사용자 인증 정보가 담겨있는지 확인할때.
