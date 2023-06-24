<template>
    <li>
        <input type="checkbox" v-model="taskCopy.completed">
        <span :class="{ completed: taskCopy.completed }">{{ taskCopy.title }}</span>
        <span class="task-info">Data: {{ taskCopy.date }} - Hora: {{ taskCopy.time }} - Categoria: {{ taskCopy.category
        }}</span>
        <p>{{ taskCopy.description }}</p>
        <button class="remove-button" @click="removeTask">Remover</button>
    </li>
</template>
  
<script>
export default {
    props: {
        task: {
            type: Object,
            required: true
        },
        index: {
            type: Number,
            required: true
        }
    },
    data() {
        return {
            taskCopy: {}
        };
    },
    mounted() {
        this.taskCopy = { ...this.task };
    },
    methods: {
        removeTask() {
            this.$emit("task-removed", this.index);
        }
    }
};
</script>
  
<style scoped>
.completed {
    text-decoration: line-through;
}
</style>
  