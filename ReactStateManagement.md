## SEB_TIL

## Props Drilling
- 리액트에서는 states(상태)를 상위컴포넌트에서 하위컴포넌트로 넘겨줘야하는데, 같은상태를 공유하는 두개의 컴포넌트가 서로다른 컴포넌트의 자식이고 이러한 tree구조가 매우커서 해당 상태를 공유할 수 있는 부모 컴포넌트와의 거리가 매우 멀게 되면, 코드의 구조가 매우 복잡해지고, 가독성또한 나빠지며 유지보수도 힘들어진다.
- 이러한 프롭스 드릴링 현상을 줄이려면 컴포넌트와 관련된 state 는 최대한 해당컴포넌트와 가깝게 위치시키거나, 상태관리 라이브러리(Redux)를 사용할 수 있다.

## 예시코드
- import React, { useState } from 'react';
import styled from 'styled-components';

const Container = styled.div`
  border: 5px solid green;
  padding: 10px;
  margin: 10px;
  position: relative;
`;

const Quantity = styled.div`
  text-align: center;
  color: red;
  border: 5px solid red;
  padding: 3px;
  font-size: 1.2rem;
`;

const Button = styled.button`
  margin-right: 5px;
`;

const Text = styled.div`
  color: ${(props) => (props.color ? props.color : 'black')};
  font-size: ${(props) => (props.size ? props.size : '1rem')};
  font-weight: ${(props) => (props.weight ? '700' : 'inherit')};
`;

export default function App() {
  const [number, setNumber] = useState(1);

  const plusNum = () => {
    setNumber(number + 1);
  };

  const minusNum = () => {
    setNumber(number - 1);
  };
  console.log('Parents');
  return (
    <Container>
      <Text weight size="1.5rem">
        [Parents Component]
      </Text>
      <Text>
        Child4 컴포넌트에 있는 버튼을 통해
        <br /> state를 변경하려고 합니다.. 🤮
      </Text>
      <Text weight color="tomato">
        Props Driling이 발생!!
      </Text>
      <Quantity>{`수량 : ${number}`}</Quantity>
      <Child1 plusNum={plusNum} minusNum={minusNum} />
    </Container>
  );
}

function Child1(
  {
    plusNum,minusNum
  }
) {
  console.log('Child1');
  return (
    <Container>
      <Text>[Child 1 Component]</Text>
      {/* plusNum, minusNum 함수를 props로 전달해주세요! */}
      <Child2 plusNum={plusNum} minusNum={minusNum}/>
    </Container>
  );
}

function Child2(
  {
    plusNum,minusNum
  }
) {
  console.log('Child2');
  return (
    <Container>
      <Text>[Child 2 Component]</Text>
      {/* plusNum, minusNum 함수를 props로 전달해주세요! */}
      <Child3 plusNum={plusNum} minusNum={minusNum}/>
    </Container>
  );
}

function Child3(
  {
    plusNum,minusNum
  }
) {
  console.log('Child3');
  return (
    <Container>
      <Text>[Child 3 Component]</Text>
      {/* plusNum, minusNum 함수를 props로 전달해주세요! */}
      <Child4 plusNum={plusNum} minusNum={minusNum}/>
    </Container>
  );
}

function Child4({ plusNum, minusNum }) {
  console.log('Child4');
  return (
    <Container>
      <Text>[Child 4 Component]</Text>
      <Button onClick={plusNum}>👍</Button>
      <Button onClick={minusNum}>👎</Button>
    </Container>
  );
}
- 위처럼 child4에 숫자를 변경시킬 수 있는 버튼이 있고, 해당 상태가 부모의 부모의 부모의 부모인 메인컴포넌트인 App컴포넌트에 선언이 되있을경우, child3,child2,child1 에 일일히 state를 넘겨줘야만 child4의 버튼이 정상적으로 동작하게된다.
- 위와같은 번거로움, 가독성문제 등을 해결하기 위해 아래의 리덕스(Redux)를 활용한 예시를 보자.
- import React, { useState } from 'react';
import styled from 'styled-components';
import { useSelector, useDispatch } from 'react-redux';

const Container = styled.div`
  border: 5px solid green;
  padding: 10px;
  margin: 10px;
  position: relative;
`;

const Quantity = styled.div`
  text-align: center;
  color: red;
  border: 5px solid red;
  padding: 3px;
  font-size: 1.2rem;
`;

const Button = styled.button`
  margin-right: 5px;
`;

const Text = styled.div`
  color: ${(props) => (props.color ? props.color : 'black')};
  font-size: ${(props) => (props.size ? props.size : '1rem')};
  font-weight: ${(props) => (props.weight ? '700' : 'inherit')};
`;

export default function App() {
  const number = useSelector((state) => state);
  console.log('Parents');
  return (
    <Container>
      <Text weight size="1.5rem">
        [Parents Component]
      </Text>
      <Text>
        Child4 컴포넌트에 있는 버튼을 통해 <br /> state를 변경하려고 합니다. ☺️
      </Text>
      <Text weight color="tomato">
        (Redux를 사용하는 경우)
      </Text>
      <Quantity>{`수량 : ${number}`}</Quantity>
      <Child1 />
    </Container>
  );
}

function Child1() {
  console.log('Child1');
  return (
    <Container>
      <Text>[Child 1 Component]</Text>
      <Child2 />
    </Container>
  );
}

function Child2() {
  console.log('Child2');
  return (
    <Container>
      <Text>[Child 2 Component]</Text>
      <Child3 />
    </Container>
  );
}

function Child3() {
  console.log('Child3');
  return (
    <Container>
      <Text>[Child 3 Component]</Text>
      <Child4 />
    </Container>
  );
}

function Child4() {
  const dispatch = useDispatch();
  const plusNum = () => {
    dispatch({ type: 'Plus' });
  };

  const minusNum = () => {
    dispatch({ type: 'Minus' });
  };
  console.log('Child4');
  return (
    <Container>
      <Text>[Child 4 Component]</Text>
      <Button onClick={plusNum}>👍</Button>
      <Button onClick={minusNum}>👎</Button>
    </Container>
  );
}
- 위코드에서처럼 react-redux의 useSelector와 useDispatch를 import해오고 관리할 상태를 메인 컴포넌트인 App에서 useSelector를 사용하여 선언후 실제로 해당 상태를 사용할 child4에서 useDispatch를 통해 상태를 불러와 사용하면 props drilling 현상을 막을 수 있다.