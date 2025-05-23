<script setup>
import { ref } from 'vue';
import './todo.css'

const todos = ref([{ id: 1, title: 'test todo' }])
const todo = ref('')
const isAddModalOpen = ref(false)

const addNewTodo = () => {
  if (todo.value.trim() === '') {
    alert('Please enter a todo title')
    return
  }
  const newTodo = {
    id: todos.value.length + 1,
    title: todo.value,
  }
  todos.value.push(newTodo)
  todo.value = ''
  isAddModalOpen.value = false
}

const deleteTodo = (id) => {
  todos.value = todos.value.filter(todo => todo.id !== id)
}

</script>

<template>
  <div class="container">
    <div class="todo-header">
      <h1>Todo App</h1>
      <button class="add-btn" @click="isAddModalOpen = true">Add todo</button>
    </div>
    <ul class="todo-list">
      <li class="todo-item" v-for="(todo) of todos" :key="todo.id">
        <span class="todo-title">{{ todo.title }}</span>
        <button class="delete-btn" @click="deleteTodo(todo.id)">x</button>
      </li>
    </ul>
    <div v-if="todos.length === 0" class="empty-todo">
      <p>No todos available</p>
    </div>
  </div>

  <div v-if="isAddModalOpen" class="modal">
    <div class="modal-content">
      <h2>Add Todo</h2>
      <input type="text" placeholder="Todo title" v-model="todo" />
      <div class="modal-actions">
        <button @click="isAddModalOpen = false" class="close-btn">Close</button>
        <button @click="addNewTodo" class="add-btn">Add</button>
      </div>
    </div>
  </div>
</template>

<style></style>
