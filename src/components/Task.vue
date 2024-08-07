<template>
  <div :class="['task-item p-5 border rounded-lg shadow-md transition-transform transform hover:scale-105', { 'border-teal-500 bg-teal-50': task.reminder }]"
    @dblclick="emit('toggle-reminder', task.id)"
  >
    <h3 class="text-xl font-semibold text-gray-800">{{ task.text }}</h3>
    <p class="text-gray-500 text-sm">{{ task.day }}</p>
    <button @click="emit('delete-task', task.id)" class="text-red-500 hover:text-red-700 transition-colors">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
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

const emit = defineEmits(['delete-task', 'toggle-reminder']);
</script>

<style scoped>
.task-item {
  background-color: #ffffff;
}
</style>
