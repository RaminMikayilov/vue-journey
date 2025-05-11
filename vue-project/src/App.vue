<script>
export default {
  data() {
    return {
      message: 'Hello Vue!',
      status: 'test',
      tasks: [
        { id: 1, name: 'Task 1' },
        { id: 2, name: 'Task 2' },
        { id: 3, name: 'Task 3' }
      ],
      googleLink: 'https://www.google.com'
    }
  }
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


</template>

<style>
h1 {
  color: #42b983;
}
</style>