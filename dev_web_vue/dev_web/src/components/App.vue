<template>
  <div class="container">
    <h1>Minhas Tarefas</h1>
    <task-form @task-added="addTask"></task-form>
    <task-list :tasks="tasks" @task-removed="removeTask"></task-list>
  </div>
</template>

<script>
import TaskForm from './TaskForm.vue';
import TaskList from './TaskList.vue';

export default {
  components: {
    TaskForm,
    TaskList
  },
  data() {
    return {
      tasks: []
    };
  },
  methods: {
    addTask(task) {
      this.tasks.push(task);
      this.saveTasksLocalStorage();
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
      this.saveTasksLocalStorage();
    },
    saveTasksLocalStorage() {
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
    getTasksFromLocalStorage() {
      const tasks = localStorage.getItem("tasks");
      this.tasks = tasks ? JSON.parse(tasks) : [];
    }
  },
  mounted() {
    this.getTasksFromLocalStorage();
  }
};
</script>

<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 20px;
  background-color: #ffffff;
  border-radius: 5px;
  box-shadow: 42px 42px 84px #aaaaaa,
    -42px -42px 84px #ffffff;
}
</style>

<style src="../style.css"></style>