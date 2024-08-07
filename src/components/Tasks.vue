<template>
    <div class="task-list space-y-4">
      <div v-for="task in tasks" :key="task.id">
        <Task :task="task" @delete-task="emit('delete-task', task.id)" @toggle-reminder="emit('toggle-reminder',task.id)" />
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  import Task from './Task.vue';
  
  const emit = defineEmits(['delete-task', 'toggle-reminder']);
  
  const props = defineProps({
    tasks: {
      type: Array,
      required: true
    }
  });
  
  </script>
  
  <style scoped>
  .task-list {
    margin-top: 20px;
  }
  </style>
  