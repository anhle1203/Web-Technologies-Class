<!-- element only render if the expression returns True values -->
<template>
    <h1>{{ message }}</h1>
    <p>
      What has keys but can't open locks, space but no room, and you can enter but
      can't go outside? What am I?
    </p>
  
    <button style="width: 200px" @click="showAnswer = !showAnswer"> <!-- 2. toggle boolean -->
      {{ !showAnswer ? 'Show me the answer!' : 'Hide the answer!' }}
    </button>
  
    <div v-if="showAnswer">A keyboard.</div>
    <!-- element using v-if will only appear in DOM tree if True-->
    <div v-show="showAnswer">A keyboard.</div>
    <!-- element using v-show always show in the DOM tree-->
  
    <!-- <div v-if="Math.random() > 0.5">Now you see me</div>
    <div v-else>Now you don't</div> -->
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  let message = ref('Hello, v-if!')
  
  let showAnswer = ref(false) // 1. initialize boolean 
  </script>
  
  <style scoped></style>