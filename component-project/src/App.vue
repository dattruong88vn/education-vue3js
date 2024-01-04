<template>
  <h4>App Text Style</h4>
  <ChildStyle />
</template>

<script>
import ChildStyle from "./components/ChildStyle.vue";

export default {
  name: "App",
  data() {
    return {
      name: "",
    };
  },
  components: { ChildStyle },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h4 {
  color: orange;
}
</style>
