# :boom: Homework

---

​																											

### 1. 아래의 설명을 읽고 T/F 여부를 작성하시오.

- Vue 프로젝트에서 상태 관리를 하기 위해서는 반드시 Vuex를 설치해야 한다.  **- F**

- mutations는 반드시 state를 수정하기 위해서만 사용되어야 한다.  **- T**

- mutations는 store.dispatch로, actions는 store.commit으로 호출할 수 있다.  **- F**

- state는 data의 역할, getters는 computed와 유사한 역할을 담당한다.  **- T**

  ​																																																																														

  ​																																																														

### 2. Vuex에서 Actions과 Mutations의 역할과, 각각에 작성되는 핸들러의 특징을 서술하시오.



**Mutations:  실제로 state를 변경하는 유일한 방법**

핸들러 함수는 반드시 동기적이어야 함

비동기적 로직은 state가 변화하는 시점이 의도한 것과 달라질 수 있으며, 콜백이 실제로 호출 될 시기를 알 수 있는 방법이 없음. 

첫번째 인자로 항상 state를 받음

Actions에서 commit() 메서드에 의해 호출됨



**Actions:  state를 변경하는 것 외에 다른 모든 동작을 맡음**

mutations와 달리 비동기 작업이 포함될 수 있음

context 객체 인자를 받음

context 객체를 통해 store.js 파일 내에 있는 모든 요소의 속성 접근, 메서드 호출이 가능

단, 가능하지만 state를 직접 변경하지는 않음

컴포넌트에서 dispatch() 메서드에 의해 호출됨





​																																																																																																																	

### 3. 컴포넌트에 작성된 Todo App 관련 코드를 Vuex의 Store로 옮기고자 한다. 빈칸에 들어갈 코드를 작성하시오.

​																																													

```javascript
export default {
  name: 'TodoList',
  data: function() {
      return {
          todoList: [],
          status: 'all',
      }
  },
  computed: {
      todoListByStatus: function(){
          return this.todoList.filter((todo) => {
              // status 값에 따라 todoList를 필터링 합니다.
          })
      },
   methods: {
       addTodo: function(){
           //새로운 todo를 todoList에 추가합니다.
       }
```

​																													

```javascript
export default new Vuex.Store({
 (a): {
    todoList: [],
    status: 'all',
  },
  (b): {
    todoListByStatus: function((d)){
        // ...
    },
  },
  (c): {
    addTodo: function((d)){
        // ...
    },
  },
```

​						

**a = state**

**b = mutations**

**c = actions**

**d = state, todo**

