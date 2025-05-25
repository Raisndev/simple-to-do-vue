<script setup lang="ts">
import { Task } from '@/types';
import { ref } from 'vue';
import TaskForm from './components/TaskForm.vue';
import TasksList from './components/TasksList.vue';

const tasks = ref<Task[]>([]);

function addTask(newTask) {
  console.log(newTask)
  tasks.value.push({
    id: crypto.randomUUID(),
    name: newTask,
    done: false
  })
}

function toggleDone(taskId) {
  const task = tasks.value.find(task => task.id === taskId)
  if(task) {
    task.done = !task.done
  }
}
</script>

<template>
  <main class="max-w-xl m-auto">
    <TaskForm @add-task="addTask"/>
    <TasksList :tasks @toggle-done="toggleDone"/>

  </main>
</template>

<style scoped>

</style>
