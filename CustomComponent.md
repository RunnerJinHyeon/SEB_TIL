## SEB_TIL

## Styled Component
- Styled Components는 앞서 배운 CSS in JS라는 개념이 대두되면서 나온 라이브러리입니다. 기존에 HTML, CSS, JS 파일로 쪼개서 개발하던 방법에서, React 등의 라이브러리의 등장으로 컴포넌트 단위 개발이 주류가 되었지만, CSS는 그렇지 못했다는 점에서 출발한 개념이죠.

- CSS in JS 라이브러리를 사용하면 CSS도 쉽게 Javascript 안에 넣어줄 수 있으므로, HTML + JS + CSS까지 묶어서 하나의 JS파일 안에서 컴포넌트 단위로 개발할 수 있게 됩니다. 이런 CSS in JS 라이브러리 중에서 현재 가장 인기 있는 라이브러리가 바로 Styled Components입니다. 이번 챕터에서는 이 Styled Components 사용법에 대해 알아보도록 합시다.

- Styled Components 설치하기
Styled Components의 설치는 간단합니다. 터미널에 아래의 명령어 한 줄을 입력해 Styled Components 라이브러리를 설치할 수 있습니다.

npm install --save styled-components@latest

import styled from "styled-components"

## Styled Component 문법
- const 컴포넌트이름 = styled.태그종류`
    CSS 속성
`



