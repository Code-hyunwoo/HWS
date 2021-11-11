# :boom: Workshop

---



​																										

### TodoList.vue			

```javascript
<template>
  <div>
    <todo-list-item
      v-for="todo in todos"
      :key="todo.date"
      :todo="todo"
    >
    </todo-list-item>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import TodoListItem from '@/components/TodoListItem'

export default {
  name: 'TodoList',
  components: {
    TodoListItem,
  },
  // 1. 과거
  // computed: {
  //   todos: function () {
  //     return this.$store.state.todos
  //   },
  // }
  // 2.
  // computed: mapState([
  //   'todos',
  // ]),
  // 3. 최종
  computed: {
    ...mapState([
      'todos'
    ])
  }
}
</script>

<style>

</style>
```

​																																

​																																																											

### TodoListitem.vue

```javascript
<template>
  <div>
    <span 
      @click="updateTodoStatus(todo)"
      :class="{ 'is-completed': todo.isCompleted }"
    >
    {{ todo.title }}
    </span>
    <button @click="deleteTodo(todo)">Delete</button>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  name: 'TodoListItem',
  props: {
    todo: {
      type: Object,
    }
  },
  methods: {
    // deleteTodo: function () {
    //   this.$store.dispatch('deleteTodo', this.todo)
    // },
    // updateTodoStatus: function () {
    //   this.$store.dispatch('updateTodoStatus', this.todo)
    // },
    ...mapActions([
      'deleteTodo',
      'updateTodoStatus',
    ])
  }
}
</script>

<style>
  .is-completed {
    text-decoration: line-through;
  }
</style>
```

​																														

### TodoForm.vue		

```javascript
<template>
  <div>
    <input 
      type="text"
      v-model.trim="todoTitle"
      @keyup.enter="creteTodo"
    >
    <button @click="creteTodo">+</button>
  </div>
</template>

<script>
export default {
  name: 'TodoForm',
  data: function () {
    return {
      todoTitle: null,
    }
  },
  methods: {
    creteTodo: function () {
      const todoItem = {
        title: this.todoTitle,
        isCompleted: false,
        date: new Date().getTime(),
      }
      // console.log('Todo create!!!')
      // this.$store.commit('CREATE_TODO', todoItem)
      if (todoItem.title) {
        this.$store.dispatch('createTodo', todoItem) // actions 호출
      }
      this.todoTitle = null
    }
  }
}
</script>

<style>

</style>
```

​																																	

### store/index.js

```javascript
import Vue from 'vue'
import Vuex from 'vuex'
import createPersistedState from "vuex-persistedstate"

Vue.use(Vuex)

export default new Vuex.Store({
  plugins: [createPersistedState()],
  state: {
    todos: []
  },
  mutations: {
    CREATE_TODO: function (state, todoItem) {
      // console.log(state)
      // console.log(todoItem)
      state.todos.push(todoItem) // state 변경
    },
    DELETE_TODO: function (state, todoItem) {
      const index = state.todos.indexOf(todoItem)
      state.todos.splice(index, 1)
    },
    UPDATE_TODO_STATUS: function (state, todoItem) {
      state.todos = state.todos.map(todo => {
        if (todo === todoItem) {
          return {
            ...todo, // JS spread syntax
            isCompleted: !todo.isCompleted
          }
        } else {
          return todo
        }
      })
    }
  },
  actions: {
    createTodo: function ({ commit }, todoItem) {
      // console.log(context)
      // console.log(todoItem)
      commit('CREATE_TODO', todoItem)
    },
    deleteTodo: function ({ commit }, todoItem) {
      commit('DELETE_TODO', todoItem)
    },
    updateTodoStatus: function ({ commit }, todoItem) {
      commit('UPDATE_TODO_STATUS', todoItem)
    }
  },
  getters: {
    completedTodosCount: function (state) {
      return state.todos.filter(todo => {
        return todo.isCompleted === true
      }).length
    },
    uncompletedTodosCount: function (state) {
      return state.todos.filter(todo => {
        return todo.isCompleted === false
      }).length
    },
    allTodosCount: function (state) {
      return state.todos.length
    },
  },
  modules: {
  }
})

```

