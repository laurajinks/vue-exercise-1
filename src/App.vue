<template>
  <div id="app">
    <!-- EX-1 -->
    <!-- 1) Fill the <p> below with your Name and Age - using Interpolation -->
    <p>{{ name }}</p>
    <!-- 2) Output your age, multiplied by 3 -->
    <p>age: {{ age * 3 }}</p>
    <!-- 3) Call a function to output a random float between 0 and 1 (Math.random()) -->
    <p>random: {{ randomFunc() }}</p>
    <!-- 4) Search any image on Google and output it here by binding the "src" attribute -->
    <div>
      <img v-bind:src="url" style="width:100px;height:100px">
    </div>
    <!-- 5) Pre-Populate this input with your name (set the "value" attribute) -->
    <div>
      <input v-bind:value="name" type="text">
    </div>
    <!-- EX-2 -->
    <!-- 1) Show an alert when the Button gets clicked -->
    <div>
      <button v-on:click="showAlert">Show Alert</button>
    </div>
    <!-- 2) Listen to the "keydown" event and store the value in a data property (hint: event.target.value gives you the value) -->
    <div>
      <input v-on:keydown="handleInput" type="text">
      <p>{{ value1 }}</p>
    </div>
    <!-- 3) Adjust the example from 2) to only fire if the "key down" is the ENTER key -->
    <div>
      <input v-on:keydown.enter="handleInput" type="text">
      <p>{{ value }}</p>
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
      url: "http://placekitten.com/g/200/200",
      value: ""
    };
  },
  methods: {
    randomFunc: function() {
      return Math.random();
    },
    showAlert: function() {
      alert("alert!");
    },
    handleInput: function() {
      this.value = event.target.value;
    }
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
