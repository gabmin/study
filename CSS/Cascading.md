## 캐스케이딩(Cascading)

CSS는 Cascading Style Sheet의 줄임말로, 캐스케이딩은 선택자에 적용된 많은 스타일 중에 어떤 스타일로 브라우저에 표현할지 결정해주는 원리를 의미한다.

캐스케이딩은 스타일 우선순위와 스타일 상속으로 나뉘며, 스타일 우선순위는 크게 3가지로 나뉜다.

<br>

### 1. 중요도

```
[ 프로그래머 CSS > 사용자 CSS > 브라우저 CSS ]
```

브라우저 CSS는 H1 태그 처럼 기본적으로 적용되어 있는 CSS를 말한다. 사용자 CSS는 흔지 않지만 웹페이지를 이용하는 사용자가 직접 CSS를 적용시킬 수 있다. 프로그래머 CSS는 웹페이지를 제작하는 제작자가 만든 CSS가 가장 높은 우선순위를 갖는다. 하지만, **!important 속성**을 이용하면 중요도를 최우선 순으로 적용시킬 수 있다.

<br>

### 2. 명시도

```
[ 인라인스타일 > id > class > 태그 ]
```

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      li {
        color: red;
      }
      #idsel {
        color: blue;
      }
      .classsel {
        color: green;
      }
    </style>
  </head>
  <body>
    <ul>
      <li>html</li>
      <li id="idsel" class="classsel" style="color:orange">css</li>
      <li>javascript</li>
    </ul>
  </body>
</html>
```

위의 예시와 같은 경우 인라인 스타일 속성인 orange 속성이 명시도가 가장 높고, 다음 id의 blue, 다음 class의 green, 다음 li태그의 red 순서대로 명시도가 적용된다.

<br>

### 3. 코드 순서

```html
<style>
  p {
    color: red;
  }

  p {
    color: blue;
  }
</style>

<div>
  <p>Hello</p>
</div>
```

코드의 순서대로 가장 마지막에 존재하는 CSS가 적용된다. 위의 예제에서는 blue 속성이 적용된다.

### 4. 스타일 상속

```html
<style>
  div {
    color: red;
  }
</style>

<div>
  <p>Hello</p>
</div>
```

위의 예시처럼 p태그에 직접적으로 스타일을 적용시키지 않았지만, 부모요소 div에 적용된 스타일이 자식요소 p태그에 적용되어 red 색상이 적용된다. 이처럼 **별도로 스타일을 지정하지 않으면 부모 요소에 있는 스타일 속성들이 자식 요소로 자동 전달되는 현상을 스타일 상속**이라고 한다.

<hr>

### 출처

https://opentutorials.org/course/2418/13409  
https://bamtory29.tistory.com/entry/CSS-Cascading-%EC%BA%90%EC%8A%A4%EC%BA%90%EC%9D%B4%EB%94%A9  
https://makinghome.tistory.com/70  
https://thrillfighter.tistory.com/487
