<script setup>
import { onMounted, ref } from 'vue';
import './todo.css'

const todos = ref([])
const todo = ref('')
const isAddModalOpen = ref(false)
const selectedTodo = ref(null)

const addNewTodo = () => {
  if (todo.value.trim() === '') {
    alert('Please enter a todo title')
    return
  }
  if (selectedTodo.value) {
    const todoToEdit = todos.value.find(t => t.id === selectedTodo.value.id)
    if (todoToEdit) {
      todos.value = todos.value.map(t => {
        if (t.id === todoToEdit.id) {
          return { ...t, title: todo.value }
        }
        return t
      })
    }
    selectedTodo.value = null
  } else {
    const newTodo = {
      id: todos.value.length + 1,
      title: todo.value,
    }
    todos.value.push(newTodo)
  }
  todo.value = ''
  isAddModalOpen.value = false
}

const deleteTodo = (id) => {
  todos.value = todos.value.filter(todo => todo.id !== id)
}

const editTodo = (id) => {
  const todoToEdit = todos.value.find(todo => todo.id === id)
  if (todoToEdit) {
    selectedTodo.value = todoToEdit
    todo.value = todoToEdit.title
    isAddModalOpen.value = true
  }
}

onMounted(() => {
  fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
    .then(response => response.json())
    .then(data => {
      todos.value = data.map(todo => ({
        id: todo.id,
        title: todo.title,
      }))
    })
    .catch(error => console.error('Error fetching todos:', error))
})

</script>

<template>
  <div class="container">
    <div class="todo-header">
      <h1>Todo App</h1>
      <button class="add-btn" @click="() => { isAddModalOpen = true; todo = ''; selectedTodo = null; }">Add
        todo</button>
    </div>
    <ul class="todo-list">
      <li class="todo-item" v-for="(todo) of todos" :key="todo.id">
        <span class="todo-title">{{ todo.title }}</span>
        <div class="todo-actions">
          <button class="edit-btn" @click="editTodo(todo.id)">v</button>
          <button class="delete-btn" @click="deleteTodo(todo.id)">x</button>
        </div>
      </li>
    </ul>
    <div v-if="todos.length === 0" class="empty-todo">
      <p>No todos available</p>
    </div>
  </div>

  <div v-if="isAddModalOpen" class="modal">
    <div class="modal-content">
      <h2>{{ selectedTodo ? 'Edit' : 'Add' }} Todo</h2>
      <input type="text" placeholder="Todo title" v-model="todo" />
      <div class="modal-actions">
        <button @click="isAddModalOpen = false" class="close-btn">Close</button>
        <button @click="addNewTodo" class="add-btn">{{ selectedTodo ?
          'Save' : 'Add' }}</button>
      </div>
    </div>
  </div>
</template>
