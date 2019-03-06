<template>
  <div id="app">
    <!-- 1) Fill the <p> below with your Name and Age - using Interpolation -->
    <p>{{ name }}</p>
    <!-- 2) Output your age, multiplied by 3 -->
    <p>age: {{ age * 3 }}</p>
    <!-- 3) Call a function to output a random float between 0 and 1 (Math.random()) -->
    <p>random: {{ Math.random() }}</p>
    <!-- 4) Search any image on Google and output it here by binding the "src" attribute -->
    <div>
      <img v-bind:src="url" style="width:100px;height:100px">
    </div>
    <!-- 5) Pre-Populate this input with your name (set the "value" attribute) -->
    <div>
      <input v-bind:value="name" type="text">
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      name: "Laura",
      age: 28,
      url: "http://placekitten.com/g/200/200"
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
