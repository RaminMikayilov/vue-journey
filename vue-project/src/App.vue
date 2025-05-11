<script>
export default {
  data() {
    return {
      message: 'Hello Vue!',
      status: 'test'
    }
  }
}
</script>

<template>
  <h1>{{ message }}</h1>
  <p v-if="status === 'active'">Active</p>
  <p v-else>Inactive</p>
</template>

<style>
h1 {
  color: #42b983;
}
</style>