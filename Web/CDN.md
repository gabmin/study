## CDN (Contents Delivery Network)

Content Delivery Network의 약자인 CDN은 지리적 제약 없이 전 세계 사용자에게 빠르고 안전하게 콘텐츠를 전송할 수 있는 콘텐츠 전송 기술을 의미한다.

CDN은 서버와 사용자 사이의 물리적인 거리를 줄여 콘텐츠 로딩에 소요되는 시간을 최소화한다. CDN은 각 지역에 캐시 서버(PoP, Points of presence)를 분산 배치해, 근접한 사용자의 요청에 원본 서버가 아닌 캐시 서버가 콘텐츠를 전달한다.

### 장점

1. 병목현상 해결  
   자주 사용되는 파일의 병목현상을 해결할 수 있다. 데이터를 항상 빠르고 안정적으로 전송할 수 있다. 또한, ISP에 장애가 발생해도 다른 ISP에 있는 캐시 서버에서 데이터를 전송하므로 전송 중단이 발생하지 않는다.

2. 트래픽 절약  
   CDN을 쓰면 트래픽이 줄어들기 때문에 서버 유지 비용도 저절로 감소한다. 원리는 caching과 비슷하다. 자주 쓰이는 파일들을 중간중간에 replica로 만들어 놓아서 클라이언트가 replica에 접근할 수 있게 한다.

### 단점

1. 특정 국가나 지역만을 타깃으로 하는 웹 서비스를 운영한다면 CDN 서비스를 활용할 필요가 없다. 이 경우 CDN을 이용하면 오히려 불필요한 연결 지점이 늘어나 웹 사이트의 성능 저하를 불러올 수 있다.

2. CDN을 위한 Cache Server들이 많이 보유되지 않거나 성능이 안정적이지 않다면 최악의 경우 SPOF(단일 장애점) 문제(즉 한 군데가 중단되면 전체 시스템이 중단되어버리는 현상)이 발생할 수 있다.

<br>

- Edge Location은 AWS의 CDN 서비스인 CloudFront를 위한 Cache Server들을 말한다. CDN Cache Server는 인터넷 트래픽을 효과적으로 처리할 수 있는 지역에 PoP을 구축하고, CDN 서비스와 사용자가 직접 만나는 곳이라고 하여 Edge라고 부르는 것이다. AWS의 Edge Location은 CDN 서비스인 CloudFront 뿐만 아리나 DNS서비스인 Route53도 함께 제공한다.

<hr>

### 출처

https://libertegrace.tistory.com/entry/Network-CDNContents-Delivery-Network-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0  
https://library.gabia.com/contents/infrahosting/8985/  
https://namu.wiki/w/CDN
