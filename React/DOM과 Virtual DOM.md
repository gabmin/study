## DOM (Document Object Model)

DOM은 HTML 문서의 계층적 구조와 정보를 표현하며 이를 제어할 수 있는 API, 즉 프로퍼티와 메서드를 제공하는 트리 자료구조이다.

```html
<div class="greeting">Hello</div>

<div>
  : 시작태그 class : 어트리뷰트 이름 (attribute name) greeting : 어트리뷰트 값
  (attribute value) Hello : 콘텐츠 (Contents)
</div>
: 종료태그
```

HTML 요소는 렌더링 엔진에 의해 파싱되어 DOM을 구성하는 요소 노드 객체로 변환된다. 어트리뷰트는 어트리뷰트 노드로, 텍스트 콘텐츠는 텍스트 노드로 변환된다.

이러한 HTML 요소 간의 부자 관계를 반영하여 HTML 문서의 구성 요소인 HTML 요소를 객체화한 모든 노드 객체들을 트리 자료 구조로 구성한다.

이처럼 노드 객체들로 구성된 트리 자료구조를 DOM이라 하며, 노드 객체의 트리로 구조화되어 있기 때문에 DOM을 DOM 트리라고 부른다.

<br>

## 가상돔(Virtual DOM)

가상돔(Virtual DOM)은 실제 DOM 문서를 추상화한 개념으로, 변화가 많은 View를 실제 DOM에서 직접 처리하는 방식이 아닌 Virtual Dom과 메모리에서 미리 처리하고 저장한 후 실제 DOM과 동기화 하는 프로그래밍 개념이다.

1. 데이터에 변화가 생겨 업데이트 되면 전체 UI를 가상돔에 리렌더링한다.
2. 변화 전후의 가상돔을 비교한다.
3. 바뀐 부분만 실제 돔에 적용을 함으로서 레이아웃 계산은 한 번만 이행된다.

![](https://media.vlpt.us/images/mollog/post/fdc15800-579c-457c-aa26-3b4c916c9c1e/image.png)

<hr>

### 출처

모던 자바스크립트 Deep Dive - 저자 이웅모  
https://velog.io/@mollog/React%EC%97%90%EC%84%9C%EC%9D%98-%EA%B0%80%EC%83%81%EB%8F%94-%EA%B0%9C%EB%85%90  
https://dev-cini.tistory.com/11
