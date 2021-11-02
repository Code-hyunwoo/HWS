# :boom: Homework

---

​																											

### 1. 아래의 설명을 읽고 T/F 여부를 작성하시오.

- Event Loop는 Call Stack이 비워지면 Task Queue의 함수를 Call Stack으로 할당하는 역할을 한다.   **T**
- XMLHttpRequest(XHR)는 AJAX요청 instance를 생성하는 JavaScript API이다. XHR의 메서드로 브라우저와 서버 간의 네트워크 요청을 전송할 수 있다.   **T**
- axios는 XHR을 보내고 응답 결과를 Promise 객체로 반환해주는 라이브러리이다.  **T**

  ​																																							

  ​																																																										

  ​																																													

### 2. 아래의 코드가 실행되었을 때 Web API, Task Queue, Call Stack 그리고 Event Loop에서 어떤 동작이 일어나는지 서술하시오.

​																																	

```javascript
console.log('Hello SSAFY!')

setTimeout(function (){
    console.log('I am from setTimeout')
}, 1000)

console.log('Bye SSAFY!')
```

​																										

1. Call Stack에서 'Hello SSAFY'를 처리하고 출력

2. setTimeout은 바로 처리할 수 없기 때문에 Web API로 넘김

3. Web API에서는 setTimeout 작업 처리하고 있음 1초

4.  Call Stack에 다음 작업 'Bye SSAFY!' 처리하고 출력

5. Web API에서 작업 완료된 setTimeout은 Task Queue로 넘겨짐

6. Call Stack이 비워진 걸 확인한 Event Loop가 setTimeout을 Call stack으로 할당

7. Call Stack에서 setTimeout 처리 'I am from setTimeout' 출력

   ​																		

   ​																																																										

### 3. JS는 Event loop를 기반으로 하는 Concurrency model을 가지고 있다고 한다. Concurrency 키워드의 특징을 작성하고, 이와 비슷한 키워드로 비교되는 Parallelism의 개념과 두 개념의 차이점을 서술하시오.

​																																												

|                 Concurrency                 |                 Parallelism                 |
| :-----------------------------------------: | :-----------------------------------------: |
|      동시에 실행되는 것 같이 보이는 것      |    실제로 동시에 여러 작업이 처리되는 것    |
| 싱글 코어에서 멀티 쓰레드를 동작시키는 방식 | 멀티 코어에서 멀티 쓰레드를 동작시키는 방식 |
|            한번에 많은 것을 처리            |            한번에 많은 일을 처리            |
|                논리적인 개념                |                물리적인 개념                |

​																						







