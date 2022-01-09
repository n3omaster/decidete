<template>
  <Decide />
  <!-- <img alt="Vue logo" src="./assets/logo.png"  <decide>/> -->
  <!-- <Counter title="Entraron" :start="50" /> -->
</template>

<script>
//import Counter from "./components/Counter.vue";
import Decide from "./components/Decide.vue";

export default {
  name: "App",
  components: {
    //Counter,
    Decide,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
