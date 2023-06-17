<template>
  <div>
   <form @submit="addTodo">
    <div class="ui input action aqui">
      <input 
        type="text" 
        v-model="title"
        placeholder="Informe a tarefa para adicionar ...">
      <input 
        type="submit" 
        value="Adicionar" 
        class="ui button purple">
    </div>
   </form>
  </div>
</template>

<script>

//import uuid from 'uuid'

export default {
  name: 'AddTodo',
  data(){
    return {
      title: ''
    }
  },

  methods: {
    addTodo(e){
      //alert(e)
      e.preventDefault();
      const newTodo = {
        //id: uuid.v4(),
        title: this.title,
        completed: false
      }

      this.$emit('add-todo', newTodo)
      this.title = ''
    }
  },
}
</script>

<style>
.aqui {
  padding: 5px;
  width: 100%;
} 
</style>
