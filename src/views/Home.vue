<template>
    <div class="container mx-auto p-6 m-6 bg-gray-100 rounded-lg shadow-lg">
      <Modal :isOpen="isModalOpen" @close="closeModal">
        <AddTask @add-task="addTask"/>
      </Modal>
      <button
      @click="openModal"
      class="bg-green-500 text-white px-4 py-2 rounded-md shadow-sm hover:bg-green-600"
    >
      Add Task
    </button>
      <Tasks :tasks="tasks" @delete-task="deleteTask" @toggle-reminder="toggleReminder" />
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  import Tasks from '../components/Tasks.vue';
  import AddTask from '../components/AddTask.vue';
  import Modal from '../components/Modal.vue';
  
  const isModalOpen = ref(false);
  const tasks = ref([]);
  
  const openModal = () => {
    isModalOpen.value = true;
  };
  
  const closeModal = () => {
    isModalOpen.value = false;
  };
  
  const fetchTasks = async () => {
    try {
      const res = await fetch('/api/tasks');
      const data = await res.json();
      tasks.value = data;
    } catch (error) {
      console.error('Failed to fetch tasks:', error);
    }
  };
  
  const addTask = async (task) => {
    try {
      const res = await fetch('/api/tasks', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(task),
      });
      const newTask = await res.json();
      tasks.value.push(newTask);
      closeModal();
    } catch (error) {
      console.error('Failed to add task:', error);
    }
  };
  
  const deleteTask = async (id) => {
    if (confirm('Are you sure you want to delete this task?')) {
      try {
        await fetch(`/api/tasks/${id}`, {
          method: 'DELETE',
        });
        tasks.value = tasks.value.filter((task) => task.id !== id);
      } catch (error) {
        console.error('Failed to delete task:', error);
      }
    }
  };
  
  const toggleReminder = async (id) => {
    const taskToToggle = tasks.value.find((task) => task.id === id);
    if (!taskToToggle) return;
  
    const updatedTask = { ...taskToToggle, reminder: !taskToToggle.reminder };
  
    try {
      const res = await fetch(`/api/tasks/${id}`, {
        method: 'PUT',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(updatedTask),
      });
      const data = await res.json();
      tasks.value = tasks.value.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      );
    } catch (error) {
      console.error('Failed to update task reminder:', error);
    }
  };
  
  onMounted(() => {
    fetchTasks();
  });
  </script>
  
  <style scoped>
  .container {
    max-width: 800px;
  }
  </style>
  