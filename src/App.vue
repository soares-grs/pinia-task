<template>
  <header>
    <img src="./assets/pinia-logo.svg" alt="Pinia Logo">
    <h1>Pinia Tasks</h1>
  </header>

  <div class="new-task-form">
    <TaskForm/>
  </div>

  <nav class="filter">
    <button @click="filter = 'all'">All tasks</button>
    <button @click="filter = 'favs'">Fav tasks</button>
  </nav>

  <div class="task-list" v-if="filter == 'all'">
    <p>You have {{ taskStore.totalCount }} tasks left to do</p>
    <div v-for="(task, index) in taskStore.tasks" :key="index">
      <TaskDetails :task="task" />
    </div>
  </div>

  <div class="task-list" v-if="filter == 'favs'">
    <p>You have {{ taskStore.favCount }} favorite tasks</p>
    <div v-for="(task, index) in taskStore.favs" :key="index">
      <TaskDetails :task="task" />
    </div>
  </div>
</template>

<script setup>
import TaskDetails from './components/TaskDetails.vue';
import TaskForm from './components/TaskForm.vue';
import { useTaskStore } from './stores/taskStore';
import { ref } from 'vue';

const taskStore = useTaskStore();
const filter = ref('all');

</script>

<style scoped></style>
