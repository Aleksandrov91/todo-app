<template>
  <div>
    <h2>Pending Tasks: ({{todos.filter(todo => {return todo.done === false}).length}})</h2>
    <todo-list v-bind:todos="pendingTasks"></todo-list>
    <h2>Completed Tasks: ({{todos.filter(todo => {return todo.done === true}).length}})</h2>
    <todo-list v-bind:todos="completedTasks"></todo-list>
  </div>
</template>

<script type="text/javascript">
import TodoList from "./../components/TodoList";

export default {
  props: ["todos"],
  components: {
    TodoList
  },
  computed: {
    pendingTasks: function() {
      return this.todos.filter(x => x.done === false);
    },
    completedTasks: function() {
      return this.todos.filter(x => x.done === true);
    }
  }
};
</script>

<style>
</style>
