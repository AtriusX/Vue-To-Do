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
  
  const storage = window.localStorage;
  
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
        storage.setItem('todos', JSON.stringify(this.todos));
      },
      addTodo(todo) {
        this.todos.push(todo)
        storage.setItem('todos', JSON.stringify(this.todos));
      }
    },
    mounted() {
      this.todos = JSON.parse(storage.getItem('todos'));
    }
  }
</script>

<style scoped>
  #app {
    margin: 10px;
  }

  * {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }
</style>
