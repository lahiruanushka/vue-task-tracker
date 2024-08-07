<template>
  <div class="container mx-auto p-6 bg-gray-100 rounded-lg shadow-lg">
    <Header title="Task Tracker" @open-modal="openModal" />
    <Modal :isOpen="isModalOpen" @close="closeModal">
      <AddTask />
    </Modal>
    <Tasks :tasks="tasks" @delete-task="deleteTask" @toggle-reminder="toggleReminder" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';
import Modal from './components/Modal.vue';

const isModalOpen = ref(false);

const openModal = () => {
  isModalOpen.value = true;
};

const closeModal = () => {
  isModalOpen.value = false;
};

const deleteTask = (id) => {
  if(confirm('Are you sure you want to delete this task?')) {
    tasks.value = tasks.value.filter((task) => task.id !== id);
  }
};

const toggleReminder = (id) => {
  tasks.value = tasks.value.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
}

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
