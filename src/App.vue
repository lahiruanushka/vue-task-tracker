<template>
  <div class="min-h-screen flex flex-col bg-gray-100">
    <Header title="Task Tracker" />
    <main class="flex-1 p-6">
      <RouterView />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import { RouterView } from 'vue-router';
import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';
</script>

<style scoped>
/* Optional global styles */
</style>
