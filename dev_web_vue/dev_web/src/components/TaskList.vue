<template>
    <ul>
      <task-item v-for="(task, index) in tasks" :key="index" :task="task" :index="index" @task-removed="removeTask"></task-item>
    </ul>
  </template>
  
  <script>
  import TaskItem from './TaskItem.vue';
  
  export default {
    components: {
      TaskItem
    },
    props: {
      tasks: {
        type: Array,
        required: true
      }
    },
    methods: {
      removeTask(index) {
        this.$emit("task-removed", index);
      }
    }
  };
  </script>
  