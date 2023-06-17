<template>
  <div id="app" class="ui container">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <div class="ui divider"></div>
    <Todos v-bind:todos="todos" />
    <div class="ui divider"></div>
  </div>
</template>

<script>

import Todos from './components/Todos.vue'
import Header from './components/layouts/Header.vue'
import AddTodo from './components/AddTodo.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo
  },

  data(){
    return {
      todos: []  
    }
  },

  methods: {
    addTodo(newTodo){
      const { title, completed } = newTodo

      axios.post('https://jsonplaceholder.typicode.com/todos?_limit=5', {
        title,
        completed
      })
      .then( res => this.todos = [...this.todos , res.data ] )
    }  
  },

  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then( res => this.todos = res.data )
    .catch( err => console.log( err ))
  }
}
</script>

<style>
#app > h1 {
  text-align: center;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  line-height: 1.4;
}

</style>
