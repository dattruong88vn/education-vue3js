<template>
  <DemoOne />
  <hr />
  <DemoTwo />
  <hr />
  <DemoThree />
</template>

<script>
import DemoOne from "./components/DemoOne.vue";
import DemoTwo from "./components/DemoTwo.vue";
import DemoThree from "./components/DemoThree.vue";

export default {
  name: "App",
  components: {
    DemoOne,
    DemoTwo,
    DemoThree,
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
