<template>
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
      <p>
        <input type="checkbox" v-on:change="markComplete">
        {{ todo.title }}
        <button 
          class="ui button red del" 
          @click="$emit('del-todo', todo.id)">
          <i class="trash icon"></i>
        </button>
      </p>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ["todo"],

  methods: {
    markComplete(){
      this.todo.completed = !this.todo.completed
    } 
  }
}
</script>

<style>
.todo-item {
  background: #f4f4f4;
  padding: 30px;
  margin-top: 2px;
  border-bottom: 1px #ccc dotted;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}  
</style>
