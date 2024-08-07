<template>
    <form @submit.prevent="onSubmit" class="space-y-6">
      <div class="form-control">
        <label class="block text-sm font-medium text-gray-700">Task</label>
        <input
          type="text"
          v-model="text"
          placeholder="Add Task"
          class="mt-1 block w-full py-2 px-3 text-base shadow-sm border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
        />
      </div>
      <div class="form-control">
        <label class="block text-sm font-medium text-gray-700">Day & Time</label>
        <input
          type="text"
          v-model="day"
          placeholder="Add Day & Time"
          class="mt-1 block w-full py-2 px-3 text-base shadow-sm border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
        />
      </div>
      <div class="form-control flex items-center">
        <label class="block text-sm font-medium text-gray-700 mr-3">Set Reminder</label>
        <input
          type="checkbox"
          v-model="reminder"
          class="h-5 w-5 text-blue-600 border-gray-300 rounded"
        />
      </div>
      <button
        type="submit"
        class="w-full bg-blue-600 text-white py-3 px-4 rounded-lg shadow-sm hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500"
      >
        Save Task
      </button>
    </form>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const text = ref('');
  const day = ref('');
  const reminder = ref(false);
  
  const onSubmit = () => {
    // Handle form submission
    console.log(text.value)
  };
  </script>