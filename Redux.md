## SEB_TIL

## Redux
- 상태관리 라이브러리

## 사용법
```javascript
//App.js
import React from 'react';
import './style.css';
// 1
import { useDispatch, useSelector } from 'react-redux';
import { increase, decrease } from './index.js';

export default function App() {
  const dispatch = useDispatch();
  // 2
  const state = useSelector((state) => state);
  // 3
  console.log(state);

  const plusNum = () => {
    dispatch(increase());
  };

  const minusNum = () => {
    dispatch(decrease());
  };

  return (
    <div className="container">
      {/* 4 */}
      <h1>{`Count: ${state}`}</h1>
      <div>
        <button className="plusBtn" onClick={plusNum}>
          +
        </button>
        <button className="minusBtn" onClick={minusNum}>
          -
        </button>
      </div>
    </div>
  );
}
```
```javascript
//index.js
import React from 'react';
import { createRoot } from 'react-dom/client';
import App from './App';
import { Provider } from 'react-redux';
import { legacy_createStore as createStore } from 'redux';

const rootElement = document.getElementById('root');
const root = createRoot(rootElement);

export const increase = () => {
  return {
    type: 'INCREASE',
  };
};

export const decrease = () => {
  return {
    type: 'DECREASE',
  };
};

const count = 1;

// Reducer를 생성할 때에는 초기 상태를 인자로 요구합니다.
const counterReducer = (state = count, action) => {
  // Action 객체의 type 값에 따라 분기하는 switch 조건문입니다.
  switch (action.type) {
    //action === 'INCREASE'일 경우
    case 'INCREASE':
      return state + 1;

    // action === 'DECREASE'일 경우
    case 'DECREASE':
      return state - 1;

    // action === 'SET_NUMBER'일 경우
    case 'SET_NUMBER':
      return action.payload;

    // 해당 되는 경우가 없을 땐 기존 상태를 그대로 리턴
    default:
      return state;
  }
  // Reducer가 리턴하는 값이 새로운 상태가 됩니다.
};

const store = createStore(counterReducer);

root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```
- index.js에서 action객체를 만들어주는 함수인 increase와 decrease를 선언후, 상태변경함수인 counterReducer함수를 선언해준다. 그리고 redux의 createStore를 활용하여 상태변경함수와 상태를 저장, App.js에서 useSelector를 사용해 index.js의 상태를 불러오고, dispatch를 사용하여 action객체생성 함수인 increase,decrease를 각각 plusNum,minusNum으로 선언.
- +버튼이 눌렸을때 plusNum실행 => increase실행 => 타입이 INCREASE인 객체생성 => counterReducer의 인자로 타입이 INCREASE인 action이 입력 => 조건문에따라서 state가 1증가 => useSelector를 통해 변경된 state가 메인 컴포넌트에도 적용 => 메인 컴포넌트의 Count값이 1증가.