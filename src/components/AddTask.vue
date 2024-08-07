<template>
  <form @submit.prevent="onSubmit" class="space-y-6 bg-white p-6 rounded-lg shadow-lg">
    <div class="form-control">
      <label class="block text-sm font-medium text-gray-700">Task</label>
      <input
        type="text"
        v-model="text"
        placeholder="Add Task"
        :class="[
          'mt-1 block w-full py-3 px-4 text-base shadow-sm border rounded-lg focus:outline-none focus:ring-2',
          textError ? 'border-red-500 focus:ring-red-500' : 'border-gray-300 focus:ring-teal-500'
        ]"
      />
      <span v-if="textError" class="text-red-500 text-sm">{{ textError }}</span>
    </div>
    <div class="form-control">
      <label class="block text-sm font-medium text-gray-700">Date</label>
      <input
        type="date"
        v-model="date"
        :class="[
          'mt-1 block w-full py-3 px-4 text-base shadow-sm border rounded-lg focus:outline-none focus:ring-2',
          dateError ? 'border-red-500 focus:ring-red-500' : 'border-gray-300 focus:ring-teal-500'
        ]"
      />
      <span v-if="dateError" class="text-red-500 text-sm">{{ dateError }}</span>
    </div>
    <div class="form-control">
      <label class="block text-sm font-medium text-gray-700">Time</label>
      <input
        type="time"
        v-model="time"
        :class="[
          'mt-1 block w-full py-3 px-4 text-base shadow-sm border rounded-lg focus:outline-none focus:ring-2',
          timeError ? 'border-red-500 focus:ring-red-500' : 'border-gray-300 focus:ring-teal-500'
        ]"
      />
      <span v-if="timeError" class="text-red-500 text-sm">{{ timeError }}</span>
    </div>
    <div class="form-control flex items-center">
      <label class="block text-sm font-medium text-gray-700 mr-3">Set Reminder</label>
      <input
        type="checkbox"
        v-model="reminder"
        class="h-5 w-5 text-teal-600 border-gray-300 rounded focus:ring-teal-500"
      />
    </div>
    <button
      type="submit"
      class="w-full bg-teal-600 text-white py-3 px-4 rounded-lg shadow-md hover:bg-teal-700 focus:outline-none focus:ring-2 focus:ring-teal-500"
    >
      Save Task
    </button>
  </form>
</template>

<script setup>
import { ref, defineEmits } from 'vue';

const text = ref('');
const date = ref('');
const time = ref('');
const reminder = ref(false);

const textError = ref('');
const dateError = ref('');
const timeError = ref('');

const emit = defineEmits(['add-task']);

const validate = () => {
  textError.value = text.value.trim() === '' ? 'Task is required' : '';
  dateError.value = date.value.trim() === '' ? 'Date is required' : '';
  timeError.value = time.value.trim() === '' ? 'Time is required' : '';

  return !textError.value && !dateError.value && !timeError.value;
};

const onSubmit = () => {
  if (validate()) {
    const newTask = {
      id: Date.now(),
      text: text.value,
      day: `${date.value} ${time.value}`,
      reminder: reminder.value
    };

    emit('add-task', newTask);

    // Reset form fields
    text.value = '';
    date.value = '';
    time.value = '';
    reminder.value = false;
  }
};
</script>

<style scoped>

</style>
