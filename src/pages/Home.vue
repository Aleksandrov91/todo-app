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
//TODO: Add link to show all pending or completed tasks. They should refer to details view.
export default {
  props: ["todos"],
  components: {
    TodoList
  },
  computed: {
    pendingTasks: function() {
      return this.todos.filter(x => x.done === false).slice(0, 10);
    },
    completedTasks: function() {
      return this.todos.filter(x => x.done === true).slice(0, 10);
    }
  }
};
</script>

<style>
</style>
