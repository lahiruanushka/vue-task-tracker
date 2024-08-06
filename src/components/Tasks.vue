<template>
    <div class="task-list space-y-4">
      <div v-for="task in tasks" :key="task.id">
        <Task :task="task" @delete-task="deleteTask" />
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  import Task from './Task.vue';
  
  const emit = defineEmits(['delete-task']);
  const props = defineProps({
    tasks: {
      type: Array,
      required: true
    }
  });
  
  const deleteTask = (id) => {
    emit('delete-task', id);
  };
  </script>
  
  <style scoped>
  .task-list {
    margin-top: 20px;
  }
  </style>
  