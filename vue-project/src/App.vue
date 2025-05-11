<script>
export default {
  data() {
    return {
      message: 'Hello Vue!',
      status: 'active',
      tasks: [
        { id: 1, name: 'Task 1' },
        { id: 2, name: 'Task 2' },
        { id: 3, name: 'Task 3' }
      ],
      googleLink: 'https://www.google.com'
    }
  },
  methods: {
    toggleStatus() {
      this.status = this.status === 'active' ? 'inactive' : 'active';
    }
  },
}
</script>

<template>
  <h1>{{ message }}</h1>
  <p v-if="status === 'active'">Active</p>
  <p v-else>Inactive</p>

  <!-- for loop -->
  <ul>
    <li v-for="task in tasks" :key="task.id">
      {{ task.name }}
    </li>
  </ul>

  <!-- v-bind example -->
  <a v-bind:href="googleLink" target="_blank">Go to the Google</a>
  <!-- shorthand for v-bind -->
  <a :href="googleLink" target="_blank">Go to the Google</a>

  <!-- v-on example -->
  <button v-on:click="toggleStatus">Change status</button>
  <!-- shorthand for v-on -->
  <button @click="toggleStatus">Change status</button>
</template>

<style>
h1 {
  color: #42b983;
}
</style>