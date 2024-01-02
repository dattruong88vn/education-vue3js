<template>
  <!-- <Components /> -->
  <div>App component username: {{ username }}</div>

  <ComponentA />
</template>

<script>
// import Components from "./components/Components.vue";
import ComponentA from "./components/nestedComponent/ComponentA.vue";

export default {
  name: "App",
  data() {
    return {
      username: "Thanh Dat",
    };
  },
  components: {
    // Components,
    ComponentA,
  },
  computed: {
    datName() {
      return "Dat Cho Dien";
    },
  },
  provide() {
    return {
      username: this.username,
      datName: this.datName,
    };
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
