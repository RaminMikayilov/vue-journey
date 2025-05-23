<script setup>
import { ref } from 'vue';

const todos = ref([{ id: 1, title: 'test todo' }])


</script>

<template>
  <div class="container">
    <div class="todo-header">
      <h1>Todo App</h1>
      <button class="add-btn">Add todo</button>
    </div>
    <ul class="todo-list">
      <li class="todo-item" v-for="(todo) of todos" :key="todo.id">
        <span class="todo-title">{{ todo.title }}</span>
        <button class="delete-btn">x</button>
      </li>
    </ul>
  </div>
</template>

<style>
.container {
  max-width: 400px;
  margin: 40px auto;
  padding: 20px;
  border-radius: 10px;
  background: #f9f9f9;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.todo-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

h1 {
  color: #42b983;
  margin-bottom: 20px;
}

.add-btn {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.2s ease;
  font-weight: bold;
}

.todo-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #ffffff;
  padding: 10px 15px;
  margin-bottom: 10px;
  border-radius: 6px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
}

.todo-title {
  font-size: 16px;
  color: #333;
}

.delete-btn {
  background-color: #ff5f5f;
  color: white;
  border: none;
  padding: 6px 10px;
  border-radius: 4px;
  cursor: pointer;
  transition: background 0.2s ease;
}

.delete-btn:hover {
  background-color: #e04848;
}
</style>
