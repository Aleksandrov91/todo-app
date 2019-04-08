<template>
  <div>
    <h2>Pending Tasks: ({{todos.filter(todo => {return todo.done === false}).length}})</h2>
    <list v-bind:todos="pendingTasks"></list>
    <h2>Completed Tasks: ({{todos.filter(todo => {return todo.done === true}).length}})</h2>
    <list v-bind:todos="completedTasks"></list>
  </div>
</template>

<script type="text/javascript">
// TODO: Rename component as Home
import List from "./../components/List";

export default {
  props: ["todos"],
  components: {
    List
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
