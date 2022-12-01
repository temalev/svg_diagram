<template>
  <div id="app">
    <CircularDigram />
  </div>
</template>

<script>
import CircularDigram from "./components/circularDigram.vue";

export default {
  name: "App",
  components: {
    CircularDigram,
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
  width: 100%;
  height: 100%;
}
html,
body {
  width: 100%;
  height: 100%;
}
</style>
