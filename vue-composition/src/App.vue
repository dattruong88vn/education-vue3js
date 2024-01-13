<template>
  <Watchers />
</template>

<script>
import Watchers from "./components/Watchers.vue";

export default {
  name: "App",
  components: {
    Watchers,
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
