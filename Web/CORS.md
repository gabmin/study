## 교차 출처 리소스 공유(Cross-Origin Resource Sharing)

### 출처(Origin)이 무엇인가?

![](https://user-images.githubusercontent.com/37062337/112098369-02762180-8be5-11eb-99ab-14b03b32d806.png)

위에 그림처럼 Protocol(Scheme), Host, Port 3가지를 합친 것을 출처(Origin)이라고 한다.

### SOP(Same-Origin-Policy)

동일출처정책 SOP는 말 그대로 "같은 출처에서만 리소스를 공유할 수 있다."라는 규칙을 가진 정책이다. 이러한 제약이 없다면 악의를 가진 사용자에 의해 CSRF나 XSS와 같은 방법으로 사용자 정보를 탈취해 갈 수 있다. 예를 들어 해커가 사용자의 정보를 탈취할 수 있는 자바스크립트 파일을 보내는 사이트게 접속하게 하여 사용자가 접속하면 그 자바스크립트 파일을 실행시켜 정보를 탈취할 수 있다. 탈취한 정보를 사용하려고 은행 사이트에 접속하려고 하면 은행 사이트는 다른 출처로부터 요청이 들어왔기때문에 SOP에 의해 CORS 오류가 발생하게 된다.

### CORS

![](https://evan-moon.github.io/static/d4d623ba331c1d7851e7000c11cd3809/6af66/cors.png)

교차 출처 리소스 공유는 추가 HTTP 헤더를 사용하여, 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제이다. 이러한 CORS는 서버가 아닌 브라우저에 구현되어 있는 스펙이다. 서버에서는 정상적으로 응답을 했지만 브라우저에서 COPS 정책에 의해 에러가 발생할 수 있다.

보통 웹 클라이언트가 다른 출처의 리소스를 요청할 때 HTTP 프로토콜을 사용하여 Header에 Origin이라는 필드에 요청을 보내는 출처를 함께 담아 보낸다. 이후 서버가 이 요청에 대한 응답을 할 때 응답 헤더의 Access-Control-Allow-Origin이라는 값에 “이 리소스를 접근하는 것이 허용된 출처”를 내려주고, 이후 응답을 받은 브라우저는 자신이 보냈던 요청의 Origin과 서버가 보내준 응답의 Access-Control-Allow-Origin을 비교해본 후 이 응답이 유효한 응답인지 아닌지를 결정한다.

### CORS 접근제어 시나리오

1.  단순요청 (Simple Request)
    단순 요청은 예비 요청을 보내지 않고 바로 서버에게 요청을 한 후, 서버가 이에 대한 응답의 헤더에 Access-Control-Allow-Origin과 같은 값을 보내주면 그때 브라우저가 CORS 정책 위반 여부를 검사하는 방식이다. 즉, 프리플라이트와 단순 요청 시나리오는 전반적인 로직 자체는 같되, 예비 요청의 존재 유무만 다르다.

        1. 요청의 메소드는 GET, HEAD, POST 중 하나여야 한다.
        2. Accept, Accept-Language, Content-Language, Content-Type, DPR, Downlink, Save-Data, Viewport-Width, Width를 제외한 헤더를 사용하면 안된다.
        3. 만약 Content-Type를 사용하는 경우에는 application/x-www-form-urlencoded, multipart/form-data, text/plain만 허용된다.

        이 3가지 특정 조건을 만족하는 경우에만 예비 요청을 생략하고 단순요청을 수행할 수 있다. 조건이 까다로워 잘 사용되지 않는다.

2.  프리플라이트 요청 (Preflight Request)
    ![](https://evan-moon.github.io/static/c86699252752391939dc68f8f9a860bf/6af66/cors-preflight.png)

        프리플라이트 방식은 요청을 한번에 보내는 것이 아닌 예비 요청과 본 요청으로 나눠 서버로 전송한다. 이러한 예비 요청을 프리플라이트라고 부르며 본 요청을 보내기 전에 브라우저 스스로 이 요청을 보내는 것이 안전한지 확인 하는 것이다.

        먼저 자바스크립트에서 브라우저에 리소스를 받아오라는 명령을 내리면 서버에게 예비 요청을 OPTIONS 메서드를 활용하여 먼저 보내고, 서버는 이 예비 요청에 대한 응답으로 현재 자신이 어떤 것들을 허용하고, 어떤 것들을 금지하고 있는지에 대한 정보를 응답 헤더에 담아서 브라우저에게 다시 보내주게 된다.

        이후 브라우저는 자신이 보낸 예비 요청과 서버가 응답에 담아준 허용 정책을 비교한 후, 이 요청을 보내는 것이 안전하다고 판단되면 같은 엔드포인트로 다시 본 요청을 보내게 된다. 이후 서버가 이 본 요청에 대한 응답을 하면 브라우저는 최종적으로 이 응답 데이터를 자바스크립트에게 넘겨준다.

3.  인증정보 포함 요청 (Credentialed Request)
    인증정보 포함 요청은 말그대로 인증된 요청을 사용하는 방법이다. 이 시나리오는 CORS의 기본적인 방식이라기 보다는 다른 출처 간 통신에서 좀 더 보안을 강화하고 싶을 때 사용하는 방법이다.

        기본적으로 브라우저가 제공하는 비동기 리소스 요청 API인 XMLHttpRequest 객체나 fetch API는 별도의 옵션 없이 브라우저의 쿠키 정보나 인증과 관련된 헤더를 함부로 요청에 담지 않는다. 이때 요청에 인증과 관련된 정보를 담을 수 있게 해주는 옵션이 바로 credentials 옵션이다.

        |옵션 값 | 설명|
        |---|---|
        |same-origin (기본값) | 같은 출처 간 요청에만 인증 정보를 담을 수 있다. |
        |include | 모든 요청에 인증 정보를 담을 수 있다|
        |omit | 모든 요청에 인증 정보를 담지 않는다|

        same-origin이나 include와 같은 옵션을 사용하여 리소스 요청에 인증 정보가 포함된다면, 이제 브라우저는 다른 출처의 리소스를 요청할 때 단순히 Access-Control-Allow-Origin만 확인하는 것이 아니라 좀 더 빡빡한 검사 조건을 추가하게 된다.

<br>
<hr>

### 출처

https://evan-moon.github.io/2020/05/21/about-cors/  
https://developer.mozilla.org/ko/docs/Web/HTTP/CORS  
https://www.youtube.com/watch?v=-2TgkKYmJt4&t=1261s
