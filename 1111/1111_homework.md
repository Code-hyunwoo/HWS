# :boom: Homework

---

​																											

### 1. 다음은 Vuex로 구성된 하나의 숫자를 counting하는 store이다.  알맞은 코드를 작성하시오.

-  NUMBER_INCREMENT  mutation handler가 호출되면 state의 count를 1만큼 증가시킨다.																				



```javascript
export default new __(a)__({
	state: {
	count: 0,
},
mutations: {
	NUMBER_INCREMENT: function (state) {
        __(b)__
    }
},
actions: {
    numberIncrement: function(context){
        __(c)__
    }
}
})
```

​							

**(a) = Vuex.store**

**(b) = state.count += 1**

**(c) context.commit('NUMBER_INCREMENT')**

​																													

​																																									

### 2. 아래 예시의 함수는 서버로부터 데이터를 가져온 뒤,  응답 값을 STATE에 저장하기 위하여 mutations를 호출하는 로직을 수행한다. 이와 같이 비동기 API 및 mutations 호출에 적합한 store의 속성 (a)를 작성하시오.



```javascript
__(a)__: {
    fetchTodoList: function({ commit }, query) {
      // commit = context.commit
      axios.get(API_URL, {
        params: {
          part: 'snippet',
          q: query,
          key: API_KEY,
          type: 'video',
        }
      })
      .then(res => {
        commit('ADD_SEARCH_RESULT', res.data.items)
      })
      .catch(err => {
        console.log(err)
      })
    },
    selectVideo: function ({ commit }, video) {
      commit('SELECT_VIDEO', video)
    }
  },
```

​																	

**actions**

​																												

​																																																																																																																	

### 3. 왼쪽처럼 store에 state, getters, actions가 정의되어 있다.  "Component Binding Helpers"를 통해 각 컴포넌트에서 사용하고자 한다.  빈칸에 들어갈 코드를 작성하시오.

​																																													

```javascript
export default new Vuex.Store({
    
  state: {    
   todoList: [],
   status: 'all',
  },
  
  getters: {
      todoListByStatus: function(state){
          //...
          })
      },
   actions: {
       createTodo: function(context){
           //...
       }
```

​																														

```javascript
import __(a)__   from __(b)__

export default {
    name: 'todoList',
    computed: {
        __(c)__([
            'todoList',
        ]),
        __(d)__([
        'todoListByStatus',
        ]),
    },
    methods: {
        __(e)__([
            'createTodo',
        ])
    }
}
```

​																

**a = {mapState,  mapGetters, mapActions}**

**b = 'vuex'**

**c = ...mapState**

**d = ...mapGetters**

**e = ...mapActions**

​																														

### 4. store에 정의한 state를 직접 변경하지 않고, mutations를 통해 변경해야 하는 이유를 작성하시오.

​																																													

Mutations 의 성격상 안에 정의한 로직들이 순차적으로 일어나야 각 컴포넌트의 반영 여부를 제대로 추적할 수가 있기 때문이다.

컴포넌트에서 직접 state 에 접근하여 변경하는 것이 아니라. Vue 의 Reactivity 체계와 상태관리 패턴에 맞지 않은 구현방식이다. 안티패턴인 이유는 여러 개의 컴포넌트에서 같은 state 값을 동시에 제어하게 되면, state 값이 어느 컴포넌트에서 호출해서 변경된건지 추적하기가 어렵기 때문이다. 하지만, 상태 변화를 명시적으로 수행함으로써 테스팅, 디버깅, Vue 의 Reactive 성질 준수 의 혜택을 얻는다.

