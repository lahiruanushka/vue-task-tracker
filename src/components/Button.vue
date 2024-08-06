<template>
    <button
      :class="['px-4 py-2 rounded text-white font-bold shadow-md transition-transform transition-colors duration-300', buttonClasses]"
      :style="{ backgroundColor: color }"
      @mouseover="hover = true"
      @mouseleave="hover = false"
      @mousedown="active = true"
      @mouseup="active = false"
    >
      {{ text }}
    </button>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  
  const props = defineProps({
    text: {
      type: String,
      required: true
    },
    color: {
      type: String,
      required: true
    }
  });
  
  const hover = ref(false);
  const active = ref(false);
  
  const buttonClasses = computed(() => {
    let baseClasses = 'bg-gray-500'; // Default color if none provided
    
    if (hover.value) {
      baseClasses = 'bg-gray-600'; // Hover color
    }
    
    if (active.value) {
      baseClasses = 'bg-gray-700'; // Active color
    }
  
    return baseClasses;
  });
  </script>
  
  
  