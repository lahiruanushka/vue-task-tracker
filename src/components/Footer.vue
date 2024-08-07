<template>
    <footer class="bg-gray-800 text-white py-4 text-center shadow-inner">
      <p class="text-sm">© {{ currentYear }} Task Tracker. All rights reserved.</p>
    </footer>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const currentYear = ref(new Date().getFullYear());
  </script>
  
  <style scoped>
  footer {
    bottom: 0;
    width: 100%;
  }
  </style>
  