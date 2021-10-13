<template>
  <div v-bind:class="{'completed': todo.completed}">
    <p v-on:click="markComplete">{{todo.title}}</p>
    <button id="btnDelete" @click="$emit('delete-todo',todo.id)">Delete</button>
  </div>
</template>
<script>
export default {
  name: 'Todo',
  props:[
      "todo"
  ],
  methods:{
    markComplete(){
      this.todo.completed = !this.todo.completed

    }
  }
}
</script>
<style scoped>
  .completed{
    text-decoration: line-through;
    text-decoration-color: red;
  }
  #btnDelete{
    font-size: small;
    background-color: red;
  }
</style>