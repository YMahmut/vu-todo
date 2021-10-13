<template>
  <div>
    <form @submit="addTodo">
      <input id="txtBox" type="text" v-model="title" name="title">
      <button id="btn" type="submit">Add</button>
    </form>
  </div>
</template>
<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodoObj = {
        id: Date.now(),
        title: this.title,
        completed: false
      }
      this.$emit('add-todo', newTodoObj);
      this.title = '';
    }
  }
}
</script>
<style scoped>
#txtBox{
  background-color: aliceblue;
  margin: 2%;
  border-radius: 2%;
}

#btn{
  background-color: aqua;
  padding: 2%;
  float: bottom;
  border-radius: 50%;
}
</style>