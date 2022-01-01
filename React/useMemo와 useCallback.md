## useMemo

```jsx
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

컴포넌트는 자신의 state가 변경되거나, 부모에게서 받는 props가 변경되었을 때마다 리렌더링 된다. (심지어 하위 컴포넌트에 최적화 설정을 해주지 않으면 부모에게서 받는 props가 변경되지 않았더라도 리렌더링 되는게 기본이다. ) 이러한 불필요한 리렌더링을 방지하기 위해 useMemo Hook을 사용한다.
**메모리제이션된 값을 반환하는 것** 이 useMemo 이다. React.memo()로 함수형 컴포넌트 자체를 감싸면 넘겨 받는 props가 변경되지 않았을 때는 상위 컴포넌트가 메모리제이션된 함수형 컴포넌트(이전에 렌더링된 결과)를 사용하게 된다.

<hr>

## useCallback

```jsx
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
```

**메모리제이션된 콜백(함수)을 반환하는 것** 이 useCallback 이다. 컴포넌트가 렌더링 될 때마다 내부에 선언되어 있던 표현식(변수, 또다른 함수 등)도 매번 다시 선언되어 사용된다. 이러한 비효율적인 반복적인 선언을 방지하고자 useCallback Hook을 사용한다.
함수는 오로지 자기 자신만이 동일하기 때문에 상위 컴포넌트에서 callback 함수를 (같은 함수이더라도) 재선언한다면 props로 callback 함수를 넘겨 받는 하위 컴포넌트 입장에서는 props가 변경 되었다고 인식한다.

<br>
<hr>

### 출처

https://www.youtube.com/watch?v=uBmnf_k7_r0  
https://leehwarang.github.io/2020/05/02/useMemo&useCallback.html
