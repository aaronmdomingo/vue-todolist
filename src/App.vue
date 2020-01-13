<template>
  <div id="app">
    <div class="main">
      <Todos v-bind:todos="todos" 
      v-on:deleteTodo="deleteTodo"
      v-on:addTodo="addTodo"/>
    </div>
  </div>
</template>

<script>
import Todos from './components/Todos'

export default {
  name: 'app',
  components: {
    Todos
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => id !== todo.id);
    },
    addTodo(toDoObj) {
      this.todos = [...this.todos, toDoObj];
    }
  },
  created() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=15')
      .then(res => res.json())
      .then(res => {
        this.todos = res;
      });
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.main {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

</style>
