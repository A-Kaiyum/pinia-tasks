<script setup>
import { ref } from 'vue';
import { useTaskStore } from './components/stores/TaskStore';
import TaskForm from './components/TaskForm.vue';
import TaskDetails from './components/TaskDetails.vue';
const taskStore = useTaskStore();
const filter = ref('all');

</script>

<template>

  <main>
  <header>
    <img src="./assets/pinia-logo.svg" alt="pinia logo">
    <h1>Pinia Tasks</h1>
  </header>
  <div class="new-task-form">
    <TaskForm />
  </div>
  <nav class="filter">
    <button @click="filter = 'all'">
      All Tasks
    </button>
    <button @click="filter = 'favs'">
      Fav Tasks
    </button>
  </nav>
  <div class="task-list" v-if="filter === 'all'">
    <p>You have {{ taskStore.totalCount }} tasks left to do</p>
    <div v-for="task in taskStore.tasks">
    <TaskDetails :task="task"/>
    </div>
  </div>
  <div class="task-list" v-if="filter === 'favs'">
    <p>You have {{ taskStore.favCount }} favs left to do</p>
     <div v-for="task in taskStore.favs">
    <TaskDetails :task="task"/>
    </div>
  </div>
  </main>
</template>

<style scoped>

</style>
