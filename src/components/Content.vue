<script></script>

<template>
  <div id="app">
    <h1>Random Movie Generator</h1>
    <button @click="generateRandomMovie">Generate Random Movie</button>
    <p v-if="randomMovie">{{ randomMovie }}</p>
  </div>
</template>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}
button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
}
button:hover {
  background-color: #45a049;
}
</style>