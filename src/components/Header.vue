<template>
  <header class="bg-blue-600 text-white p-4 rounded-t-lg shadow-md flex items-center justify-between">
    <h1 class="text-2xl font-semibold">{{ title }}</h1>
    <button @click="$emit('open-modal')" class="bg-green-500 text-white px-4 py-2 rounded-md shadow-sm hover:bg-green-600">
      Add Task
    </button>
  </header>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  title: {
    type: String,
    required: true
  }
});
</script>

<style scoped>
/* Optional custom styles */
</style>
