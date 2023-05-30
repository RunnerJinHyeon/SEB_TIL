## SEB_TIL

## State 끌어올리기
- 하위 컴포넌트의 클릭이벤트가 부모의 상태를 바꾸어야 하는 상황에 상태를 변경시키는 함수를 하위컴포넌트에 props로 전달하여 해결가능.
- 상위 컴포넌트안의 State 변경함수를 리턴문에 있는 하위 컴포넌트에 예를들어<Childcomponent onClickButton = {State변경함수}/> 처럼 props 형태로 전달 후에 하위 컴포넌트에서 function Childcomponent({onClickButton}) 와 같이 인자로 해당 props를 받은 후 onClickButton 함수를 상위 컴포넌트의 State변경함수로써 사용가능하다.