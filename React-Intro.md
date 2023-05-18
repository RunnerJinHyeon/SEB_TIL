## SEB_TIL

## React INTRO
- 2023년 5월 18일
- 리액트는 자바스크립트 코드 하나만으로 html,javascript 두 코드의 기능을 구현할 수 있는 라이브러리이다.
- 기존에 html 로 태그를 작성 후 해당 태그를 자바스크립트에서 document.queryselector 를 이용해서 하나하나 상호작용 코드를 넣어줬다면, React 를 활용하면 이러한 번거로움을 해소할 수 있다.

## React 쓰는법
- import React from "react";
import "./styles.css";

function App() {
  const user = {
    firstName: "React",
    lastName: "JSX Activity"
  };

  function formatName(user) {
    return user.firstName + " " + user.lastName;
  }
  

  // JSX 를 활용한 React
  return <h1>Hello, {formatName(user)}!</h1>;
}

export default App;
- 위처럼 App 이라는 컴포넌트 안에 리턴문으로 html 형태의 코드를 작성하여 사용 가능하다.
- 기본적으로 리액트는 외부 라이브러리이기 때문에 사용하기전에 npm install을 통해 설치를 해야한다.

