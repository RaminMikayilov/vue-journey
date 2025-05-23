<script setup>
import { ref } from 'vue';

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
        <button class="delete-btn">x</button>
      </li>
    </ul>
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
  margin: 0;
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

.delete-btn,
.add-btn,
.close-btn {
  border: none;
  padding: 10px 15px;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.2s ease;
  font-weight: bold;
}

.add-btn {
  background-color: #42b983;
  color: white;
}

.add-btn:hover {
  background-color: #36a372;
}

.delete-btn {
  background-color: #ff5f5f;
  color: white;
  padding: 6px 10px;
}

.delete-btn:hover {
  background-color: #e04848;
}

.close-btn {
  background-color: #ff5f5f;
  color: white;
  margin-right: 10px;
}

.close-btn:hover {
  background-color: #e04848;
}

/* Modal Styles */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 10px;
  width: 300px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.modal-content h2 {
  color: #42b983;
  margin-bottom: 15px;
}

.modal-content input {
  width: 100%;
  padding: 8px 10px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 6px;
}

.modal-actions {
  display: flex;
  justify-content: flex-end;
}
</style>
