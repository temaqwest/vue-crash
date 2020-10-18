<template>
  <div id="app">
    <h1>Todo List</h1>
    <todoAdd
      @add-todo="addTodo"
    />
    <hr>
    <todoListComponent
      v-bind:todos="todos"
      @remove-todo="removeTodo"
    />
  </div>
</template>

<script>

import todoListComponent from '@/components/todoListComponent'
import todoAdd from '@/components/todoAdd'

export default {
  name: 'App',
  data() {
    return {
      todos: [
        { id: 1, title: "Shopping at Shaw's Grocery Store", completed: false },
        { id: 2, title: "Meeting with a dentist", completed: false },
        { id: 3, title: "Meeting at Wires Beach", completed: false },
        { id: 4, title: "Kanye West concert (Armenian Church, 20 Oct, 9pm)", completed: false },
      ]
    }
  },

  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
    .then(response => response.json())
    .then(json => { this.todos = json })
  },

  components: {
    todoListComponent,
    todoAdd
  },

  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter( t => t.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
