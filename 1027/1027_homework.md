# :boom: Homework

---

​																											

### 1. 아래의 설명을 읽고 T/F 여부를 작성하시오.

- document.createElement메서드를 통해 HTML 요소를 생성할 수 있다.  **T**
- EventTarget.addEventListener(type, listener)에서 listener 위치에 콜백 함수를 정의한다.
  이때 콜백 함수의 첫 번째 매개변수에는 발생한 이벤트에 대한 정보를 담고 있는 Event 객체가 전달된다.  **T**
- event.preventDefault 메서드를 통해 이벤트 동작을 취소할 수 있다.   **T**
- 부모 노드에서 자식노드를 추가하는 유일한 방법은 append 메서드 뿐이다. **F**

​																																				

​																															

### 2. DOM Event에는 다양한 종류의 event가 존재한다.

### 아래 제시된 Event들이 각각 어떤 시점에 발생하는지 

### MDN 문서를 참고하여 간단하게 작성하시오.

​																																

click      **클릭했을 때**

mouserover   **마우스가 리스너가 등록된 엘리먼트나 그 자식 엘리먼트 위로 이동했을 때**

mouserout    **마우스가 리스너가 등록된 엘리먼트 밖으로 이동했을 때**

keydown   **키가 눌렸을 때**

keyup       **키 누름이 해제될 때**

load       **리소스와 그 의존 리소스의 로딩이 끝났을 때**

scroll    **document, element가 스크롤 되었을 때**

change      **폼 컨트롤(value의 값)이나 요소의 값이 변경 되었을 때** 

input      **사용자가 값을 수정할 때마다 발생**

​																							

​																											

### 3. 콘솔창을 통해 메세지를 확인하는 코드 완성하시오.

​																							

```html
const button = document.(a)('button')

button.(b)((c), function (){
	console.log('Button clicked!')
})
```

**a = querySelector**

**b = addEventListener**

**c = 'click'**

