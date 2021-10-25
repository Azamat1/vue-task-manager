<template>
  <div class="layout">
    <div id="app">
      <TodoForm v-on:create-todo="handleCreateTodo" />
      <TabsPanel v-bind:tabs="tabs" v-on:tab-change="handleTabChange">
        <TodoList v-if="activeTab === 'today'" v-bind:todos="todosToday" v-on:remove-todo="handleRemoveTodo" />
        <TodoList v-if="activeTab === 'income'" v-bind:todos="todosIncome" v-on:remove-todo="handleRemoveTodo" />
        <TodoList v-if="activeTab === 'week'" v-bind:todos="todosWeek" v-on:remove-todo="handleRemoveTodo" />
      </TabsPanel>
      
    </div>
  </div>
</template>

<script>
import TodoForm from "./components/TodoForm.vue";
import TodoList from "./components/TodoList.vue";
import TabsPanel from "./components/UI/TabsPanel.vue";
import './global.css';

export default {
  name: "App",
  components: {
    TodoForm,
    TodoList,
    TabsPanel
  },
  data() {
    return {
      todos: [
        { text: "1", id: Date.now(), type: 'today' },
        { text: "2", id: Date.now() + 1, type: 'today' },
      ],
      activeTab: 'today',
      tabs: ['today', 'income', 'week']
    };
  },
  computed: {
    todosToday: function() {
      return this.todos.filter(todo => todo.type === 'today')
    },
    todosIncome: function() {
      return this.todos.filter(todo => todo.type === 'income')
    },
    todosWeek: function() {
      return this.todos.filter(todo => todo.type === 'week')
    }
  },
  methods: {
    handleCreateTodo: function (text) {
      this.todos.push({ text: text, id: Date.now(), type: this.activeTab });
    },
    handleRemoveTodo: function (id) {
      console.log("handleRemoveTodo", id);
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    handleTabChange: function (tab) {
      this.activeTab = tab
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  border: 0;
  max-width: 860px;
}

.layout {
  padding: 10px 20px;
  display: flex;
  justify-content: center;
}
</style>
