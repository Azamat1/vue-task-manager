<template>
  <form @submit.prevent>
    <input class="input" type="text" v-model="todo.text" />
    <br /><button class="add_btn" title="Create" v-on:click="$emit('create-todo', todo.text)">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      todo: {
        text: "",
      },
    };
  },
};
</script>

<style>
.input {
  width: 400px;
}
.add_btn {
  margin-top: 10px;
  width: 400px;
  height: 20px;
}
</style>
