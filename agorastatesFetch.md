## SEB_TIL

## fetch 활용

### 기존 아고라스테이츠 클라이언트에 서버연결
- let agoraStatesDiscussions;
fetch("http://localhost:4000/discussions").then(res=>res.json()).then(json=>{
  agoraStatesDiscussions = json;
  render(ul);
  console.log(agoraStatesDiscussions);
})
- fetch를 활용하여 서버예습때 완성한 서버를 연결.
- localhost:4000에 연결
- 기존에 사용하던 data.js(더미데이터) 를 클라이언트 html과의 연결 해제.
- 서버실행 후 클라이언트 html 실행하면 서버에있는 discussions가 화면에 출력.