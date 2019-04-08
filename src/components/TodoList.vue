<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>

    <todo
      v-on:delete-todo="deleteTodo"
      v-on:complete-todo="completeTodo"
      v-for="todo in todos"
      v-bind:todo="todo"
      v-bind:key="todo.title"
    ></todo>
  </div>
</template>

<script type="text/javascript">
import Todo from "./Todo";

export default {
  props: ["todos"],
  components: {
    Todo
  },
  methods: {
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
      this.$notify({
        group: "app",
        type: "success",
        title: "Success",
        text: `${todo.title} todo has been completed!`
      });
    },
    deleteTodo(todo) {
      swal({
        title: "Are you sure?",
        text: "Once deleted, you will not be able to recover this todo!",
        icon: "warning",
        buttons: true,
        dangerMode: true
      }).then(willDelete => {
        if (willDelete) {
          const todoIndex = this.todos.indexOf(todo);
          this.todos.splice(todoIndex, 1);

          this.$notify({
            group: "app",
            type: "success",
            title: "Success",
            text: "Your todo has been deleted!"
          });
        }
      });
    }
  }
};
</script>

<style>
</style>
