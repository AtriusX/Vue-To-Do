<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>
  import AddTodo from './components/layout/AddTodo'
  import Header from './components/layout/Header'
  import Todos from './components/Todos'
  export default {
    name: 'app',
    components: {
      AddTodo,
      Header,
      Todos
    },
    data() {
      return {
        todos: []
      }
    },
    methods: {
      deleteTodo(id) {
        this.todos = this.todos.filter(t => t.id != id);
      },
      addTodo(todo) {
        this.todos.push(todo)
      }
    }
  }
</script>

<style scoped>
  #app {
    margin: 10px;
  }
</style>
