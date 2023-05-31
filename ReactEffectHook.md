## SEB_TIL

## Side Effect
- 함수 외부의 상태나 변수를 변화시키는 함수를 side effect(부수효과) 가 있는 함수라고 칭한다.
- 순수함수는 side effect가 없는 함수의 입력만이 함수의 결과에 영향을 주는 함수이다.
- React의 함수 컴포넌트는 props 가 입력으로 JSX Element가 출력으로 나감으로써 side effect 가 없는 순수함수이다.
- 하지만 AJAX 요청이나 Localstorage와 같은 리액트와 상관없는 API는 리액트 입장에선 side effect 이다.

## useEffect
- 리액트의 side effect함수를 실행을 위한 Effect Hook이다.
- 첫번째 인자(parameter)는 실행시킬 side effect함수.
- 두번째 인자는 첫번째 인자의 함수를 실행시킬 조건의 배열이다.(아무것도 없으면 컴포넌트혹은 프롭스가 업데이트 될때마다 실행, 빈배열이면 처음 랜더링때만 실행, 배열안에 조건이 있으면 해당 조건이 변경될때만 실행.)