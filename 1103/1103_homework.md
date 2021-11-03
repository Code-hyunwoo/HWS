# :boom: Homework

---

​																											

### 1. 아래의 설명을 읽고 T/F 여부를 작성하시오.

- SPA는 Single Pattern Application의 약자이다.   **-  F**

- SPA 은 웹 어플리케이션에 필요한 모든 정적 리소스를 한번에 받고, 이후부터는 페이지 갱신에 필요한 데이터만 전달 받는다.  **- T**

- Vue.js 에서 말하는 반응형 이라는 것은 데이터가 변경되면 이에 반응하여 연결된 DOM이 업데이트 되는 것을 의미한다.  **-  T**

  

  ​																																																																														

  ​																																																														

### 2. MVVM 은 무엇의 약자인지 작성하고 , 해당 패턴에서 각 파트의 역할은 무엇인지 간단히 서술하시오.



**Model- View - ViewModel** 의 약자이다.

Model - JavaScript Object. JavaScript의 Object 자료 구조

View - DOM(HTML).   Data의 변화에 따라서 바뀌는 대상

ViewModel - 모든 Vue Instance. View와 Model 사이에서 Data와 DOM에 관련된 모든 일 처리																			

​																												

​																																																																																				

### 3. 다음의 빈칸 (a), (b), (c) 에 들어갈 코드를 작성하시오

​																																													

```javascript
<div id="app">
    {{ (a) }}
</div>
<script>
	const app = (b) ({
        el: (c),
        data : {
            message: 'hello World!',
        },
    })
</script>

```

​																													

**a = message**

**b = new Vue**

**c = #app**

