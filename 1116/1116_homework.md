# :boom: Homework

---

​																											

### 1. 아래의 설명을 읽고 T/F 여부를 작성하시오.

- DRF Server는 단순히 요청에 따라 데이터 및 인증을 처리하는 등의 역할만 담당할 뿐 반드시 Vue가 Client일 필요는 없다.   **- F**

-  Vue & DRF가 기존에 Django만 사용했을 때와 다른 점은 Django의 MTV 중 Template 부분을 Vue가 대체한 것이다.   **- T**

- 같은 localhost에서 활성화 되어있는 Django와 Vue.js 서버는 서로 제약없이 리소스를 요청하고 응답 받을 수 있다.    **- F**

  


​																													

​																																									

### 2. Sever-Client 구조의 애플리케이션에서 사용자 인증 기능을 구현하고자 한다.  Client는 Vue 그리고 Server 는 DRF를 이용하여 구현했다고 할 때, DRF에서 지원하는 세션인증 방식과 토큰 인증 방식의 차이점을 서술하시오.

​										

토큰 인증 방식은 Server 메모리에 정보를 저장하지 않아 server의 자원 절약이 가능하고,

상대적으로 HTML, HTTP 환경에서 사용하기 용이하다.

또한 토큰 인증 방식은 데이터베이스에서 유효성 검사가 필요없다.





​																													

​																																																																																																																	

### 3. DRF Server에서 JWT 인증 방식을 이용하여 사용자 인증 기능을 구현했다고 하자.
이 때, Client에서 인증이 필요한 API endpoint로 요청을 보내기 위해서는 JWT 값을
HTTP __(a)__ request header에 실어서 요청을 보내야 한다.
__(a)__ request header의 이름과 특징을 작성하시오.

​																																													

 HTTP Authorization header

Header는 토큰의 타입과 해시 암호화 알고리즘으로 구성되어 있습니다. 첫째는 토큰의 유형 (JWT)을 나타내고, 두 번째는 HMAC, SHA256 또는 RSA와 같은 해시 알고리즘을 나타내는 부분입니다.
Payload는 토큰에 담을 클레임(claim) 정보를 포함하고 있습니다. Payload 에 담는 정보의 한 ‘조각’ 을 클레임이라고 부르고, 이는 name / value 의 한 쌍으로 이뤄져있습니다. 토큰에는 여러개의 클레임 들을 넣을 수 있습니다.
클레임의 정보는 등록된 (registered) 클레임, 공개 (public) 클레임, 비공개 (private) 클레임으로 세 종류가 있습니다.
마지막으로 Signature는 secret key를 포함하여 암호화되어 있습니다.

​								
