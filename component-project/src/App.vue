<template>
  <Parent />
</template>

<script>
import Parent from "./components/slots/Parent.vue";
export default {
  name: "App",
  data() {
    return {
      name: "",
    };
  },
  components: { Parent },
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
