<template>
  <div id="app">
    <notifications group="app"/>
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:add-todo="addTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from "./components/TodoList";
import CreateTodo from "./components/CreateTodo";

export default {
  name: "app",
  components: {
    TodoList,
    CreateTodo
  },
  data() {
    return {
      todos: [
        {
          title: "Todo A",
          project: "Project A",
          description:
            "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem",
          done: false
        },
        {
          title: "Todo B",
          project: "Project B",
          description:
            "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem",
          done: true
        },
        {
          title: "Todo C",
          project: "Project C",
          description:
            "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem",
          done: false
        },
        {
          title: "Todo D",
          project: "Project D",
          description:
            "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem",
          done: false
        }
      ]
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
      this.$notify({
        group: "app",
        type: "success",
        title: "Success",
        text: "Your todo has been created!"
      });
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
