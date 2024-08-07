<template>
  <header class="bg-gradient-to-r from-blue-500 to-teal-500 text-white p-5 shadow-lg flex items-center justify-between rounded-b-lg">
    <h1 class="text-3xl font-bold">{{ title }}</h1>
    <nav class="flex space-x-6">
      <RouterLink
        to="/"
        class="text-white hover:bg-blue-600 px-3 py-2 rounded-md transition-colors"
        :class="{ 'bg-blue-700': isActiveLink('/') }"
      >
        Home
      </RouterLink>
      <RouterLink
        to="/about"
        class="text-white hover:bg-blue-600 px-3 py-2 rounded-md transition-colors"
        :class="{ 'bg-blue-700': isActiveLink('/about') }"
      >
        About
      </RouterLink>
    </nav>
   
  </header>
</template>

<script setup>
import { defineProps } from 'vue';
import { RouterLink, useRoute } from 'vue-router';

const isActiveLink = (routePath) => {
  const route = useRoute();
  return route.path === routePath;
};

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
