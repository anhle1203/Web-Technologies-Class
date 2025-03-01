<template>
    <h1>{{ message }}</h1>
    <button @click="sortUsersByAge">Sort users by age</button>
    <button @click="hideInactiveUsers">Hide inactive users</button>
    <button @click="showFirstTwoUsers">Show first two users</button>
    <ul>
      <li v-for="(user, index) in users" :key="user.id">
        {{ index }} - {{ user.id }} - {{ user.name }} - {{ user.age }} -
        {{ user.isActive }}
      </li>
    </ul>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  let message = ref('Hello, Array Change Detection!')
  
  const users = ref([
    { id: 1001, name: 'John Smith', age: 26, isActive: false },
    { id: 1002, name: 'Tom Doe', age: 16, isActive: false },
    { id: 1003, name: 'Frankin Wong', age: 18, isActive: true }
  ])
  
  function sortUsersByAge() {
    users.value.sort((a, b) => a.age - b.age)
  }
  
  // Slice/Concat/Filter are non-mutating array methods in the array so we need to update the array by assignment.
  function hideInactiveUsers() {
    users.value = users.value.filter((user) => user.isActive) // Assignment to update the array in app.devtools
  }
  
  function showFirstTwoUsers() {
    users.value = users.value.slice(0, 2) // Slicing to get the first two users
  }

  // CAUTION: These actions may cause data loss
  </script>
  
  <style scoped>
  .inactive {
    color: red;
    text-decoration: line-through;
  }
  </style>