<template>
  <div id="app">
    <TodoForm 
      v-on:create-todo="onCreateTodo"
    />
    <TodoList
      v-bind:todos="todos"
      v-on:remove-todo="onRemoveTodo"
    />
  </div>
</template>

<script>
import TodoForm from './components/TodoForm.vue'
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoForm, TodoList
  },
  data() {
    return {
      todos: [
        { text: '1', id: Date.now() },
        { text: '2', id: Date.now() + 1 }
      ]
    }
  },
  methods: {
    onCreateTodo: function (text) {
      this.todos.push({ text: text, id: Date.now() })
    },
    onRemoveTodo: function (id) {
      console.log('onRemoveTodo', id)
      this.todos = this.todos.filter(todo => todo.id !== id)
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
  margin-top: 60px;
}
</style>
