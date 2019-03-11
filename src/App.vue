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
    <hr>
    <!-- EX-4 -->
    <!-- 1) Start the Effect with the Button. The Effect should alternate the "highlight" or "shrink" class on each new setInterval tick (attach respective class to the div with id "effect" below) -->
    <div>
      <button @click="startEffect">Start Effect</button>
      <div id="effect" :class="effectClasses"></div>
    </div>
    <!-- 2) Create a couple of CSS classes and attach them via the array syntax -->
    <div>
      <input type="text" v-model="userClass">
      <div v-bind:class="['visible', userClass]"></div>
    </div>
    <!-- 4) Let the user enter a class and enter true/ false for another class (create some example classes) and attach the classes -->
    <div>
      <input type="text" v-model="userClass">
      <input type="text" v-model="visible">
      <div :class="[{visible: visible}, userClass]"></div>
    </div>
    <!-- 5) Repeat 3) but now with values for styles (instead of class names). Attach the respective styles.  -->
    <div>
      <input type="text" v-model="myStyle.backgroundColor">
      <div :style="myStyle"></div>
    </div>
    <!-- 6) Create a simple progress bar with setInterval and style bindings. Start it by hitting the below button. -->
    <div>
      <button @click="startProgress">Start Progress</button>
      <div :class="['progressBar']" :style="progressBar"></div>
    </div>
    <hr>
    <div id="exercise">
      <!-- 1) Hook up the button to toggle the display of the two paragraphs. Use both v-if and v-show and inspect the elements to see the difference -->
      <div>
        <button @click="toggleParagraph">Toggle</button>
        <p v-if="showParagraph">You either see me ...</p>
        <p v-else>...or me</p>
        <p v-show="showParagraph">You either see me ...</p>
        <p v-show="!showParagraph">...or me</p>
      </div>
      <!-- 2) Output an <ul> of array elements of your choice. Also print the index of each element. -->
      <ul>
        <li v-for="(name, i) in array" :key="i">{{ name }} {{ i }}</li>
      </ul>
      <!-- 3) Print all key-value pairs of the following object: {title: 'Lord of the Rings', author: 'J.R.R. Tolkiens', books: '3'}. Also print the index of each item. -->
      <ul>
        <li v-for="(value, key) in myObject" :key="key">{{ key }}: {{ value }}</li>
      </ul>
      <!-- 4) Print the following object (only the values) and also create a nested loop for the array: {name: 'TESTOBJECT', data: [1.67, 1.33, 0.98, 2.21]} (hint: use v-for and v-if to achieve this) -->
      <ul>
        <li v-for="value in testData" :key="value">
          <template v-if="Array.isArray(value)">
            <div v-for="element in value" :key="element">{{element}}</div>
          </template>
          <template v-else>{{value}}</template>
        </li>
      </ul>
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
      count: 0,
      effectClasses: {
        highlight: false,
        shrink: true
      },
      userClass: "",
      visible: false,
      myStyle: {
        width: "100px",
        height: "150px",
        backgroundColor: "gray"
      },
      progressBar: {
        width: "0px",
        backgroundColor: "purple"
      },
      array: ["Max", "Anna", "Chris", "Manu"],
      myObject: {
        title: "Lord of the Rings",
        author: "J.R.R. Tolkiens",
        books: "3"
      },
      testData: {
        name: "TESTOBJECT",
        id: 10,
        data: [1.67, 1.33, 0.98, 2.21]
      },
      showParagraph: true
    };
  },
  computed: {
    result: function() {
      return this.count > 37 ? "Greater than 37" : "Not greater than 37";
    }
  },
  watch: {
    count: function() {
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
    },
    startEffect: function() {
      const vm = this;
      setInterval(function() {
        vm.effectClasses.highlight = !vm.effectClasses.highlight;
        vm.effectClasses.shrink = !vm.effectClasses.shrink;
      }, 2000);
    },
    startProgress: function() {
      const vm = this;
      var width = 0;
      setInterval(function() {
        width = width + 10;
        vm.progressBar.width = width + "px";
      }, 300);
    },
    toggleParagraph: function() {
      this.showParagraph = !this.showParagraph;
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

#effect {
  width: 100px;
  height: 100px;
  border: 1px solid black;
}

.highlight {
  background-color: red;
  width: 200px !important;
}

.shrink {
  background-color: gray;
  width: 50px !important;
}

.blue {
  background: blue;
}

.visible {
  width: 100px;
  height: 100px;
}

.fontSize {
  font-size: 40px;
}

.example {
  background: gray;
  border: 1px solid hotpink;
  width: 30px;
  height: 30px;
}

.progressBar {
  /* background: purple; */
  height: 30px;
  width: 200px;
  border: 1px solid black;
}
</style>
