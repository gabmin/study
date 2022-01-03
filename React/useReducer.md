## useReducer

```jsx
const [<상태 객체>, <dispatch 함수>] = useReducer(<reducer 함수>, <초기 상태>, <초기 함수>)
```

useReducer는 현재 상태(state) 객체와 행동(action) 객체를 인자로 받아서 새로운 상태(state) 객체를 반환하는 함수이다. usestate와 비슷하게 상태를 관리할때 사용하지만, Hook 함수를 사용하면 컴포넌트의 상태 업데이트 로직을 컴포넌트에서 분리시킬 수 있다. 마치 상태관리 라이브러리를 활요하는 것과 유사하다.

- 예시

```jsx
import React, { useReducer } from "react";

function reducer(state, action) {
  switch (action.type) {
    case "INCREMENT":
      return state + 1;
    case "DECREMENT":
      return state - 1;
    default:
      return state;
  }
}

function Counter() {
  const [number, dispatch] = useReducer(reducer, 0);

  const onIncrease = () => {
    dispatch({ type: "INCREMENT" });
  };

  const onDecrease = () => {
    dispatch({ type: "DECREMENT" });
  };

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={onIncrease}>+1</button>
      <button onClick={onDecrease}>-1</button>
    </div>
  );
}
```

<br>
<hr>

### 출처

https://react.vlpt.us/basic/20-useReducer.html
