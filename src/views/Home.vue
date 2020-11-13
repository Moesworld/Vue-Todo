<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todo v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import AddTodo from '../components/AddTodo.vue'
import Todo from '../components/Todo.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    AddTodo,
    Todo
  }, 
  data() {
    return {
      todos: [
     
      ]
    }
  },
  methods: {
    deleteTodo(id){

      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(this.todos = this.todos.filter(todo => todo.id !== id))
      .catch(err => console.log(err));
      //this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo){
      const {id, title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {id, title, completed})
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));
     
    }
  }, 
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=3').then(res => this.todos = res.data).catch(err => console.log(err));
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