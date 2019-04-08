<template>
  <div class="ui basic content center aligned segment">
    <button class="ui basic button icon" v-on:click="openForm" v-show="!isCreating">
      <i class="plus icon"></i>
    </button>
    <div class="ui centered card" v-show="isCreating">
      <div class="content">
        <div class="ui form">
          <div class="field">
            <label>Title</label>
            <input v-model.trim="titleText" type="text" ref="title" defaultValue>
          </div>
          <div class="field">
            <label>Project</label>
            <input v-model.trim="projectText" type="text" ref="project" defaultValue>
          </div>
          <div class="field">
            <label>Description</label>
            <textarea
              v-model.trim="todoContent"
              type="text"
              ref="description"
              defaultValue
              rows="3"
            ></textarea>
          </div>
          <div class="ui two button attached buttons">
            <button class="ui basic blue button" v-on:click="sendForm()">Create</button>
            <button class="ui basic red button" v-on:click="closeForm()">Cancel</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  data() {
    return {
      titleText: "",
      projectText: "",
      todoContent: "",
      isCreating: false
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText;
        const project = this.projectText;
        const description = this.todoContent;

        this.$emit("add-todo", {
          title,
          project,
          description,
          done: false
        });

        this.titleText = "";
        this.projectText = "";
        this.todoContent = "";
      }

      this.isCreating = false;
    }
  }
};
</script>

<style>
</style>
