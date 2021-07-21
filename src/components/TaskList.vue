<template>
  <main>
    <div class="toolbar">
      <h3>Tasks</h3>
      <button class="btn text" @click="toggleFilter">
        {{ filter === "all" ? "Show Incomplete" : "Show All" }}
      </button>
    </div>
    <ul v-if="filteredTasks.length">
      <task
        v-for="task in filteredTasks"
        :key="task.id"
        :task="task"
        @toggle-complete-task="(id) => $emit('toggle-complete-task', id)"
      ></task>
    </ul>
    <h4 class="no-tasks-message" v-else>
      You don't have any tasks. Start adding by clicking "New Task"
    </h4>
  </main>
</template>

<script>
import Task from "./Task.vue";

export default {
  components: { Task },
  name: "TaskList",
  props: {
    tasks: Array,
  },
  data() {
    return {
      filter: "all",
    };
  },
  computed: {
    filteredTasks() {
      if (this.filter === "incomplete") {
        return this.tasks.filter((task) => !task.done);
      } else if (this.filter === "all") {
        return this.tasks;
      }
      return this.tasks;
    },
  },
  methods: {
    toggleFilter() {
      this.filter === "all"
        ? (this.filter = "incomplete")
        : (this.filter = "all");
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  max-height: 250px;
  overflow: hidden auto;
}
.toolbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}
.no-tasks-message {
  text-align: center;
}
</style>