<template>
  <div>
    <h2>{{ customTitle }} {{ start }}</h2>
    <p>{{ counter }} <sup>2</sup> = {{ counter * counter }}</p>
    <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>

    <div>
      <button @click="increase">+1</button>
      <button @click="decrease">-1</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    start: {
      type: Number,
      default: 0,
      required: false,
      validator (value) {
          return value >= 10
      }
    },
    title: {
      type: String,
      default: "Título",
      required: false,
    },
  },
  methods: {
    getSquareValue() {
      console.log("getSquareValue");
      return this.counter * this.counter;
    },
    increase() {
      console.log("increase");
      this.counter++;
    },
    decrease() {
      console.log("decrease");
      this.counter--;
    },
  },
  name: "Contador",
  data() {
    return {
      counter: this.start,
    };
  },
  computed: {
    squareCounter() {
      console.log("squareCounter");
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title ? this.title : "Computada";
    },
  },
};
</script>

<style>
button {
  margin: 0 5px;
}
</style>