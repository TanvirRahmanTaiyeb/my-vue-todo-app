<template>
    <!-- The main application template -->
    <div class="app">
      <h1>My Meaningful Todo List</h1>
      <!-- Container for adding new tasks -->
      <div class="add-task-container">
        <!-- Input field for new tasks -->
        <input
          v-model="newTodo"
          @keyup.enter="addTodo"
          placeholder="Enter a new task..."
        />
        <!-- Button to add new tasks -->
        <button @click="addTodo" class="add-task-button">Add Task</button>
      </div>
      <!-- List of tasks -->
      <ul>
        <li v-for="(todo, index) in todos" :key="index" :class="{ 'completed': todo.completed, 'deleted': todo.deleted }">
          <!-- Checkbox to mark task as completed -->
          <input type="checkbox" v-model="todo.completed">
          <!-- Task text -->
          <span>{{ todo.text }}</span>
          <!-- Button to delete task -->
          <button @click="toggleDeleteStatus(todo)">Delete</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        // Input for new task
        newTodo: '',
        // Array to store tasks
        todos: []
      };
    },
    methods: {
      // Method to add a new task
      addTodo() {
        if (this.newTodo.trim() === '') return;
        this.todos.push({ text: this.newTodo, completed: false, deleted: false });
        this.newTodo = '';
      },
      // Method to toggle task's delete status
      toggleDeleteStatus(todo) {
        todo.deleted = !todo.deleted;
      }
    }
  };
  </script>
  
  <style>
  /* Styling for the component */
  body {
    font-family: 'Arial', sans-serif;
    background-color: #f0f0f0;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
  }
  
  .app {
    max-width: 500px;
    width: 90%;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    padding: 20px;
    box-sizing: border-box;
  }
  
  /* Styles for other elements */
  /* ... (scroll down for the rest of the styles) ... */
  
  h1 {
    margin: 0 0 20px;
    font-size: 32px;
    color: #333;
    text-align: center;
  }
  
  .add-task-container {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .add-task-button {
    background-color: #44c767;
    color: #fff;
    border: none;
    border-radius: 8px;
    padding: 10px 20px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .add-task-button:hover {
    background-color: #3aaf5f;
  }
  
  input[type="text"] {
    width: 100%;
    padding: 12px;
    border: none;
    border-radius: 8px;
    background-color: #f4f4f4;
    margin-bottom: 10px;
    font-size: 16px;
    color: #555;
    transition: background-color 0.3s;
  }
  
  input[type="text"]:focus {
    background-color: #e0e0e0;
  }
  
  ul {
    list-style: none;
    padding: 0;
  }
  
  li {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 12px;
    background-color: #f9f9f9;
    border-radius: 8px;
    margin-bottom: 10px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    transition: background-color 0.3s, transform 0.3s;
  }
  
  li:hover {
    background-color: #f0f0f0;
    transform: translateY(-2px);
  }
  
  .completed {
    text-decoration: line-through;
    color: #999;
  }
  
  .deleted {
    display: none;
  }
  
  button {
    background-color: #ff6666;
    color: #fff;
    border: none;
    border-radius: 4px;
    padding: 6px 12px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  button:hover {
    background-color: #ff4d4d;
    transform: scale(1.05);
  }
  </style>
  