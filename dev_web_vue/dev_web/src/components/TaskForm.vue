<template>
    <div class="add-task">
      <form>
        <input type="text" v-model="newTask.title" placeholder="Digite o nome da tarefa...">
        <textarea v-model="newTask.description" placeholder="Digite a descrição da tarefa..."></textarea>
        <input type="date" v-model="newTask.date">
        <input type="time" v-model="newTask.time">
        <select v-model="newTask.category">
          <option disabled value="">Selecione a categoria</option>
          <option v-for="(category, index) in categories" :value="category" :key="index">{{ category }}</option>
        </select>
        <button @click="addTask">Adicionar</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTask: {
          title: "",
          description: "",
          date: "",
          time: "",
          category: ""
        },
        categories: ["Faculdade", "Trabalho", "Pessoal"]
      };
    },
    methods: {
      addTask() {
        if (this.newTask.title.trim() !== "") {
          this.$emit("task-added", { ...this.newTask, completed: false });
          this.resetNewTask();
        }
      },
      resetNewTask() {
        this.newTask = {
          title: "",
          description: "",
          date: "",
          time: "",
          category: ""
        };
      }
    }
  };
  </script>
  
  <style scoped>

  </style>


