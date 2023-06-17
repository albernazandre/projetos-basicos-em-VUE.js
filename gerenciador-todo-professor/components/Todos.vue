<template>
  <div>
    <div v-for="todo in todos" v-bind:key="todo.id">
      <TodoItem v-bind:todo="todo" v-on:del-todo="deleteTodo" />
    </div>
  </div>
</template>

<script>

import TodoItem from './TodoItem.vue'
import axios from 'axios'

export default {
  name: 'Todos',
  components: {
    TodoItem
  },
  props: ["todos"],
  methods: {
    deleteTodo(id){
      //alert("Tá funcionando o botão de deletar: " + id)
      
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then( this.todos = this.todos.filter( todo => todo.id !== id ) )
      .catch( err => console.log(err))
    } 
  }
}
</script>

<style>
  
</style>
