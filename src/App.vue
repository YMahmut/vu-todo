<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>
<script>
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'app',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Learn Js',
          completed: false
        },
        {
          id: 2,
          title: 'Learn Vue',
          completed: false
        },
        {
          id: 3,
          title: 'Write assay',
          completed: false
        }
      ],
    }
  },
  methods: {
    addTodo(newTodoObj) {
      this.todos = [...this.todos, newTodoObj];

      if (newTodoObj.title == '') {
        setTimeout(() => alert("CAN NOT BE EMPTY !!"));
        this.deleteTodo(newTodoObj.id);
      }

    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id != todoId);
    }
  },
  mounted() {
    let todo = this.todos.find(x => x.id === 2)
    console.log(todo)
  }
}
</script>
<style>
</style>