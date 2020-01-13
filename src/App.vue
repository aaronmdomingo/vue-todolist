<template>
  <div id="app">
    <div class="main">
      <Todos v-bind:todos="filteredList"
      v-on:deleteTodo="deleteTodo"
      v-on:addTodo="addTodo"
      v-on:searchTodo="searchTodo"/>
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
      search: '',
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => id !== todo.id);
    },
    addTodo(toDoObj) {
      this.todos = [...this.todos, toDoObj];
    },
    searchTodo(searchStr) {
      this.search = searchStr;
    }
  },
  created() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=15')
      .then(res => res.json())
      .then(res => {
        this.todos = res;
      });
  },
  computed: {
    filteredList() {
        return this.todos.filter(todo => todo.title.includes(this.search));
    }
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