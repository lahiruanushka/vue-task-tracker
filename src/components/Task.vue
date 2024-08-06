<template>
    <div :class="['task-item p-4 border rounded-lg shadow-sm', { 'border-green-500': task.reminder }]">
      <h3 class="text-xl font-semibold">{{ task.text }}</h3>
      <p class="text-gray-600">{{ task.day }}</p>
      <button @click="onDelete(task.id)" class="text-red-500 hover:text-red-700">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
        </svg>
      </button>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    task: {
      type: Object,
      required: true
    }
  });
  
  const emit = defineEmits(['delete-task']);
  
  const onDelete = (id) => {
    emit('delete-task', id);
  };
  </script>
  
  <style scoped>
  .task-item {
    background-color: #fff;
  }
  </style>
  