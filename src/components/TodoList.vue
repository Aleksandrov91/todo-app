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
    },
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    }
  }
};
</script>

<style>
</style>
