<template>
  <div class="container mx-auto p-6 bg-gray-100 rounded-lg shadow-lg">
    <Header title="Task Tracker" />
    <Tasks :tasks="tasks" @delete-task="deleteTask" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';

const deleteTask = (id) => {
  console.log(id);
};

const tasks = ref([
  {
    id: 1,
    text: 'Doctors Appointment',
    day: 'March 1st at 2.30pm',
    reminder: true
  },
  {
    id: 2,
    text: 'Meeting at School',
    day: 'March 2nd at 1.30pm',
    reminder: true
  },
  {
    id: 3,
    text: 'Food Shopping',
    day: 'March 3rd at 12.00pm',
    reminder: true
  },
  {
    id: 4,
    text: 'Dentist Appointment',
    day: 'March 4th at 3.00pm',
    reminder: true
  },
  {
    id: 5,
    text: 'Prepare Presentation',
    day: 'March 5th at 5.00pm',
    reminder: false
  }
]);
</script>

<style scoped>
.container {
  max-width: 800px;
}
</style>
