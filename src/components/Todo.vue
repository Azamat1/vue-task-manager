<template>
  <li class="todo" v-on:click="$emit('remove-todo', id)">
    {{ text }}
  </li>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      required: true,
    },
    id: {
      type: Number,
      required: true,
    },
  }
};
</script>

<style>
.todo {
  border: 1px solid rgb(233, 160, 50);
  padding: 5px;
  margin-top: 10px;
}
</style>