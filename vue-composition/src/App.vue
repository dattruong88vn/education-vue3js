<template>
  <ClickCount />
  <HoverCount />
</template>

<script>
import ClickCount from "./components/ClickCount.vue";
import HoverCount from "./components/HoverCount.vue";

export default {
  name: "App",
  components: {
    ClickCount,
    HoverCount,
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
