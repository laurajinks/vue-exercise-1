<template>
  <div id="app">
    <div id="exercise">
   <!-- 1) Fill the <p> below with your Name and Age - using Interpolation -->
    <p>VueJS is pretty cool - YOUR_NAME (AGE)</p>
    <!-- 2) Output your age, multiplied by 3 -->
    <p></p>
    <!-- 3) Call a function to output a random float between 0 and 1 (Math.random()) -->
    <p></p>
    <!-- 4) Search any image on Google and output it here by binding the "src" attribute -->
    <div>
        <img style="width:100px;height:100px">
    </div>
    <!-- 5) Pre-Populate this input with your name (set the "value" attribute) -->
    <div>
        <input type="text">
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  data: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
