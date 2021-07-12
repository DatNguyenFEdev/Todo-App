<template>
  <div id="app">
    <div id="todoapp">      
      <TodoApp />
    </div>
  </div>
</template>

<script>
import TodoApp from './components/TodoApp'
export default {
  name: 'App',
  data() {
    return {
      todo: '',
      todos: [
        {

        }
      ]
    }
  },
  methods: {
    addTodo() {
      this.todo = this.todos;
    }
  },
  components: {
    TodoApp
  }
}
</script>

<style>
body {
  background-color: black;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
