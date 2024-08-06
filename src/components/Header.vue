<template>
    <header class="bg-blue-600 text-white p-4 rounded-t-lg shadow-md flex items-center justify-between">
      <h1 class="text-2xl font-semibold">{{ title }}</h1>
      <Button text="Add Task" color="#4CAF50" />
    </header>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  import Button from '@/components/Button.vue';
  
  const props = defineProps({
    title: {
      type: String,
      required: true
    }
  });
  </script>
  