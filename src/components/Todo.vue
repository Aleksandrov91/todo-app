<template>
  <div class="three wide column">
    <div class="ui centered card">
      <div class="content" v-show="!isEditing">
        <div class="header">{{todo.title}}</div>
        <div class="meta">Project: {{todo.project}}</div>
        <div class="description">{{todo.description}}</div>
        <div class="extra-content">
          <span class="right floated trash icon" v-on:click="deleteTodo(todo)">
            <i class="trash icon"></i>
          </span>
          <span class="right floated edit icon" v-on:click="showForm">
            <i class="edit icon"></i>
          </span>
        </div>
      </div>

      <div class="content" v-show="isEditing">
        <div class="ui form">
          <div class="field">
            <label>Title</label>
            <input type="text" v-model="todo.title">
          </div>
          <div class="field">
            <label>Project</label>
            <input type="text" v-model="todo.project">
          </div>
          <div class="field">
            <label>Description</label>
            <textarea v-model="todo.description" rows="3"></textarea>
          </div>
          <div class="ui two attached buttons">
            <button class="ui basic blue button" v-on:click="hideForm(todo)">Close X</button>
          </div>
        </div>
      </div>

      <div class="ui bottom attached green basic button" v-show="todo.done">Completed</div>
      <div
        class="ui bottom attached red basic button"
        v-on:click="completeTodo(todo)"
        v-show="!todo.done"
      >Complete</div>
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  props: ["todo", "isEditing"],
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm(todo) {
      this.isEditing = false;
      todo.done = false;
    },
    completeTodo(todo) {
      this.$emit("complete-todo", todo);
    },
    deleteTodo(todo) {
      this.$emit("delete-todo", todo);
    }
  }
};
</script>

<style>
</style>
