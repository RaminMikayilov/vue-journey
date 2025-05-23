<script setup>
import { ref } from 'vue';

const status = ref('active');
const message = ref('Hello Vue 3 + Vite!');

const toggleStatus = () => {
  status.value = status.value === 'active' ? 'inactive' : 'active';
  message.value = `Status changed to ${status.value}`;
}
</script>

<template>
  <h1>{{ message }}</h1>
  <p v-if="status === 'active'">Active</p>
  <p v-else>Inactive</p>

  <button @click="toggleStatus">Change status</button>
</template>

<style>
h1 {
  color: #42b983;
}
</style>