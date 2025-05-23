## CORS(Cross Origin Resource Sharing)
CORS는 출처가 다른 곳의 리소스를 요청할 때 접근 권한을 부여하는 메커니즘이다.
출처는 URL뿐만 아니라 프로토콜과 포트까지 포함.
클라이언트의 출처가 허용되지 않았다면 CORS 에러가 발생할 수 있다. 프록시 서버를 이용해서 직접적으로 리소스를 요청하지 않는 방법을 사용해 CORS 에러를 피할 수 있음.

### CORS는 왜 필요한가?
과거에 크로스 사이트 요청 위조(CSRF, Cross Site Request Forgery) 문제가 있었다. 

CSRF를 예방하기 위해 브라우저는 동일한 출처 정책(SOP)을 구현했다. SOP가 구현된 브라우저는 클라이언트와 동일한 출처의 리소스로만 요청을 보낼 수 있다.

하지만 보통은 다른 출처의 리소스를 사용하는 경우가 많다.
따라서 SOP를 확장한 CORS가 필요하다.

### CORS의 작동
#### Simple Request

브라우저가 요청 메시지에 Origin 헤더와 응답 메시지의 Access-Control-Allow-Origin 헤더를 비교해서 CORS를 위반하는지 확인한다.
Origin에는 현재 요청하는 클라이언트의 출처(프로토콜, 도메인, 포트)가, Access-Control-Allow-Origin은 리소스 요청을 허용하는 출처가 작성.

#### Preflight Request

브라우저가 사전 요청을 보내는 경우. 브라우저가 본 요청을 보내기 이전, Preflight Request를 OPTIONS 메서드로 요청을 보내어 실제 요청이 안전한지 확인한다.

Preflight Request는 추가로 Access-Control-Request-Method로 실 요청 메서드와, Access-Control-Request-Headers 헤더에 실 요청의 추가 헤더 목록을 담아 보낸다.

