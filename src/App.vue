<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todo v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import AddTodo from './components/AddTodo.vue'
import Header from './components/layouts/Header.vue'
import Todo from './components/Todo.vue'

export default {
  name: 'App',
  components: {
    Header,
    AddTodo,
    Todo
  }, 
  data() {
    return {
      todos: [
        {
          id: 1, 
          title: "Todo One",
          completed: false
        },{
          id: 2, 
          title: "Todo two",
          completed: false
        },{
          id: 3, 
          title: "Todo Three",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo){
      this.todos = [...this.todos, newTodo]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
