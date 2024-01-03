<template>
  <Input v-model="name" />
</template>

<script>
import Input from "./components/vmodelCustomComponent/Input.vue";

export default {
  name: "App",
  data() {
    return {
      name: "",
    };
  },
  components: {
    Input,
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
