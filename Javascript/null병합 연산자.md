## null 병합 연산자

null 병합 연산자 ??는 좌항의 피연사자가 null 또는 undefined인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다. null 병합 연산자는 변수에 기본값을 설정할 때 유용하다.

```jsx
let foo = null ?? "default string";
console.log(foo); //'default string'

let poo = 0 ?? "default string";
console.log(poo); // 0
```

병합 연산자는 좌항의 피연산자가 false로 평가되는 Falsy 값을(false,0,-0,'')이면 좌항의 피연산자를 그대로 반환한다.

<hr>

### 출처

모던 자바스크립트 Deep Dive - 저자 이웅모
