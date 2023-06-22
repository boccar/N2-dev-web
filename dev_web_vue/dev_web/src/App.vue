<template>
  <div class="container">
    <h1>Minhas Tarefas</h1>
    <div class="add-task">
      <input type="text" v-model="newTask.title" placeholder="Digite o nome da tarefa...">
      <textarea v-model="newTask.description" placeholder="Digite a descrição da tarefa..."></textarea>
      <input type="date" v-model="newTask.date">
      <input type="time" v-model="newTask.time">
      <select v-model="newTask.category">
        <option disabled value="">Selecione a categoria</option>
        <option v-for="(category, index) in categories" :value="category" :key="index">{{ category }}</option>
      </select>
      <button @click="addTask">Adicionar</button>
    </div>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <input type="checkbox" v-model="task.completed">
        <span :class="{ completed: task.completed }">{{ task.title }}</span>
        <span class="task-info">Data: {{ task.date }} - Hora: {{ task.time }} - Categoria: {{ task.category }}</span>
        <p>{{ task.description }}</p>
        <button class="remove-button" @click="removeTask(index)">Remover</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [],
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
        this.tasks.push({ ...this.newTask, completed: false });
        this.newTask.title = "";
        this.newTask.description = "";
        this.newTask.date = "";
        this.newTask.time = "";
        this.newTask.category = "";
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>
<style src="./style.css" scoped></style>