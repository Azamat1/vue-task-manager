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
  width: 800px;
    border: 1px solid brown;
    height: 40px;
    font-size: 2.4rem;
}
.add_btn {
  margin-top: 10px;
  width: 25.6rem;
  height: 4rem;
}

</style>
