<template>
  <ul>
    <Todo
      v-on="$listeners"
      v-for="(todo, index) in todos" 
      v-bind:key="index"
      v-bind:text="todo.text"
      v-bind:id="todo.id"
    >
    </Todo>
  </ul>
</template>

<script>
import Todo from './Todo.vue'

export default {
  components: {
    Todo
  },
  props: {
      todos: {
          type: Array,
          required: true
      }
  },
}
</script>

<style>

</style>