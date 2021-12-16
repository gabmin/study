## SPA (Single Page Application)

90년대에는 대부분 Static Site로 클라이언트가 서버에 요청을 보내면 서버에 만들어져 있는 HTML파일을 응답하여 보내게 된다. 하지만, 클라이언트에서 페이지 동작을 할 때 마다 서버로 부터 HTML파일을 받아와야 하기 때문에 UI/UX 적으로 좋지 않다.

이후 iframe 태그가 도입되면서 전체 HTML파일을 요청하는 것이 아닌 부분적으로 문서를 받아와 파일을 업데이트 하는 방식이 가능하게 되었다.

XMLHttpRequest API가 개발되면서 더이상 HTML파일 전체를 받아오는 것이 아닌 JSON형식과 같은 데이터만 받아 자바스크립트를 통해 동적으로 페이지를 업데이트 하는 방식이 나타나게 되었다.

이러한 방식이 AJAX라는 이름을 갖게 되었고, SPA가 널리 사용되게 되었다.

![](https://miro.medium.com/max/550/0*pTpSpu-YP5QiPq7R.png)

<br>

## 클라이언트 사이드 렌더링(Client Side Rendering)

전통적인 방식의 SPA가 사용하는 렌더링 방식으로 클라이언트가 첫 요청시 index.html파일을 응답하는데, 이 파일은 텅비어져 있고 Root id와 어플리케이션에 필요한 자바스크립트 링크만 들어가 있다. 그래서 처음 접속시 빈 화면만 보이게 되고 이후 링크된 자바스크립트 app.js파일을 받아오게 되는데, 이 파일은 모든 데이터가 담겨있어 용량이 커 처음 다운로드 받는데 많은 시간이 소요되게 된다. app.js파일을 다 받아오게 되면 화면에 렌더링 되기 시작한다. 이후 SPA의 특성대로 필요한 데이터는 JSON형식으로 받아와 동적으로 업데이트하여 렌더링한다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2Fra7J3%2FbtrhgjWvkT5%2FNDgW2v7Zkpj4pJvjuDhQdk%2Fimg.png)

- 장점

1. 초기 요청을 제외하면 빠른 페이지 전환과 더 나은 UX/UI를 제공한다.
2. 서버에 요청하는 횟수가 적어 서버 부담이 적다.

- 단점

1. 최초 로딩 시 모든 리소스들을 받아와서 초기 로딩 속도가 느리다.
2. 처음에 HTML이 비어있어 크롤러가 데이터를 수집할 수 없기에 SEO(검색 엔진 최적화) 문제가 발생한다.
3. 쿠키나 localStorage에서 사용자에 대한 정보를 저장해야 하기 때문에 XSS 공격에 취약하다.

<br>

## 서버 사이드 렌더링(Server Side Rendering)

CSR의 단점을 보완하고자 SSR이 개발되었다. 서버 사이드 렌더링은 클라이언트에서 요청을 하면, 서버에서 필요한 데이터를 모아 HTML파일을 만들고 이 파일과 약간의 JS소스코드와 함께 응답을 한다. 그래서 HTML파일이 바로 렌더링 되어 클라이언트 측에서는 받아온 HTML파일을 즉시 볼 수 있다. 페이지 이동이 생길때마다 서버에 요청을 해서 HTML파일을 받아와야 한다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FmlVRS%2Fbtrhc7pGX3W%2F2pqahv1NC02FkF1dWcvve0%2Fimg.png)

- 장점

1. CSR에 비해 다운 받는 파일이 많지 않아 초기 로딩 속도가 빨라 사용자가 빨리 컨텐츠를 볼 수 있다.
2. HTML에 대한 정보가 처음부터 포함되어 있어 모든 검색엔진에 대한 SEO(검색엔진 최적화)가 가능

- 단점

1. Static Site 처럼 매번 페이지를 요청할 때마다 새로고침 되기 때문에 깜빡거리는 듯한 현상이 생겨 UX/UI가 다소 떨어짐
2. 페이지를 이동할 때마다 매번 서버에 요청을 하기 때문에 서버의 부하가 커짐
3. 빠르게 초기 화면을 볼 수 있지만 JS파일을 다운받기 전까지 동작에 문제가 발생할 수 있다.

<br>
<hr>

### 출처

https://medium.com/iotrustlab/%EC%9B%B9-spa-single-page-application-%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-ba9e26ad1cc5  
https://koras02.tistory.com/m/85  
https://www.youtube.com/watch?v=iZ9csAfU5Os&t=333s
