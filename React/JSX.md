## JSX

Javascript 확장 문법으로 JSX는 **React “엘리먼트(element)”** 를 생성한다.

```js
function App(){
    return React.createElement("div", null, "Hello", React.createElement("b", null, "World!!")
}
```

위와 같은 자바스크립트 코드처럼 React.createElement 매번 써야하는 것은 매우 불편하다. 그래서 아래와 같은 JSX를 활용하여 코드를 작성한다.
JSX는 자바스크립트 안에서 HTML 문법을 사용해서 view를 구성할 수 있게 도와주는 자바스크립트 문법으로 리액트 개발에 매우 편리하다.
JSX로 작성한 코드는 브라우저에서 시행되기 전에 코드가 번들링되는 과정에서 바벨을 통해 일반 자바스크립트 형태의 코드로 변환된다.

```jsx
function App() {
  return (
    <div>
      Hello <b> World!!</b>
    </div>
  );
}
```

엘리먼트는 React 앱의 가장 작은 단위이다. 브라우저 DOM 엘리먼트와 달리 React 엘리먼트는 일반 객체이며(plain object) 쉽게 생성할 수 있다. React 엘리먼트는 불변객체이다. 엘리먼트를 생성한 이후에는 해당 엘리먼트의 자식이나 속성을 변경할 수 없다. React DOM은 React 엘리먼트와 일치하도록 DOM을 업데이트한다. 즉, React DOM은 해당 엘리먼트와 그 자식 엘리먼트를 이전의 엘리먼트와 비교하고 DOM을 원하는 상태로 만드는데 필요한 경우에만 DOM을 업데이트한다.

<br>

## JSX 규칙

### 1. 자바스크립트 표현식 포함

```jsx
const hello = <h1> 안녕하세요, {name} 님! </h1>;
```

중괄호를 사용하여 JSX안에서 Javascript 표현식을 사용할 수 있다.

<br>

### 2. className

```jsx
const element = <h1 className="greeting">Hello, world!</h1>;
```

HTML에서 Class를 사용했지만, ES6의 클래스 문법과 겹치는 예약어이기 때문에 className을 사용해야 한다.

<br>

### 3. 엘리먼트

```jsx
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

리액트에서는 반드시 상위 태그로 감싸져 있어야 한다. 여러개의 태그가 존재하면 오류가 발생한다. 반드시 하나의 엘리먼트만 반환해야한다.

<br>

### 4. inLine Style

```html
<p style="color: orange; font-size: 20px;">orange</p>
```

```jsx
<p style={{ color: "orange", fontSize: "20px" }}>orange</p>;

//혹은 스타일 딕셔너리를 변수로 만들고 쓸 수 있다.
function App() {
  const styles = {
    color: "orange",
    fontSize: "20px",
  };

  return (
    <div className="App">
      <p style={styles}>orange</p>
    </div>
  );
}
```

<br>
<hr>

### 출처

https://ko.reactjs.org/docs/rendering-elements.html  
https://developerntraveler.tistory.com/54  
https://velog.io/@edie_ko/React-JSX%EB%9E%80-%EB%A0%8C%EB%8D%94%EB%A7%81-Rendering%EC%9D%B4%EB%9E%80
