<template>
  <form class="section" v-if="open" @submit.prevent="submitTask">
    <div class="form-control">
      <label for="task">Task</label>
      <input type="text" id="task" v-model="task" />
    </div>
    <div class="form-control">
      <label for="date">Date</label>
      <input type="date" id="date" v-model="date" />
    </div>
    <input type="submit" class="btn" value="Add Task" :disabled="!task" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  props: {
    open: Boolean,
  },
  data() {
    return {
      task: "",
      date: "",
    };
  },
  methods: {
    submitTask() {
      if (task.value) {
        this.$emit("add-task", { task: this.task, date: this.date });
        this.task = "";
        this.date = "";
      }
    },
  },
};
</script>

<style scoped>
.section {
  margin-bottom: 32px;
}
</style>