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
      <img :src="url" style="width:100px;height:100px">
    </div>
    <!-- 5) Pre-Populate this input with your name (set the "value" attribute) -->
    <div>
      <input :value="name" type="text">
    </div>
    <hr>
    <!-- EX-2 -->
    <!-- 1) Show an alert when the Button gets clicked -->
    <div>
      <button @click="showAlert">Show Alert</button>
    </div>
    <!-- 2) Listen to the "keydown" event and store the value in a data property (hint: event.target.value gives you the value) -->
    <div>
      <input @keydown="handleInput" type="text">
      <p>{{ value }}</p>
    </div>
    <!-- 3) Adjust the example from 2) to only fire if the "key down" is the ENTER key -->
    <div>
      <input @keydown.enter="handleInput" type="text">
      <p>{{ value }}</p>
      <!-- Use 2 way data binding to update value -->
      <input v-model="value" type="text">
      <p>{{ value }}</p>
    </div>
    <hr>
    <!-- EX-3 -->
    <!-- 1) Show a "result" of 'not there yet' as long as "value" is not equal to 37 - you can change "value" with the buttons. Print 'done' once you did it -->
    <div>
      <p>Current Value: {{ count }}</p>
      <button @click="count += 5">Add 5</button>
      <button @click="count += 1">Add 1</button>
      <p>{{ result }}</p>
    </div>
    <!-- 2) Watch for changes in the "result" and reset the "value" after 5 seconds (hint: setTimeout(..., 5000) -->
    <div>
      <input type="text">
      <p>{{ count }}</p>
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
      value: "",
      count: 0
    };
  },
  computed: {
    result: function() {
      return this.count > 37 ? "Greater than 37" : "Not greater than 37";
    }
  },
  watch: {
    count: function(value) {
      const vm = this;
      setTimeout(function() {
        vm.count = 0;
      }, 2000);
    }
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
