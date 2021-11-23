## pointer-events 속성

pointer-events 는 HTML 요소들의 마우스/터치 이벤트들(CSS hover/active, JS click/tap, 커서 드래그등)의 응답을 조정할 수 있는 속성이다.

<br>

### 숨김 처리 속성에 따른 특성

| 숨김 속성과 값      | 공간점유               | 이벤트 | 탭 접근 |
| ------------------- | ---------------------- | ------ | ------- |
| opacity:0           | 점유                   | 활성   | 가능    |
| visibility:hidden   | 점유                   | 비활성 | 불가능  |
| visibility:collapse | 테이블 안에서만 비점유 | 비활성 | 불가능  |
| display:none        | 비점유                 | 비활성 | 불가능  |

<br>

### 예시

```
pointer-events: "none"
pointer-events: "all"
pointer-events: "auto"
pointer-events: "inherit"
```

### 출처

https://webclub.tistory.com/331  
https://developer.mozilla.org/ko/docs/Web/CSS/pointer-events
