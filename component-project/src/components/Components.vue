<template>
  <Greet name="Bruce" hero-name="Batman" />
  <Greet name="Clark" hero-name="Superman" />
  <Greet name="Diana" hero-name="Wonder Woman" />
  <Greet :name="name" :hero-name="heroName" />
</template>

<script>
import Greet from "./Greet.vue";

export default {
  name: "component",
  components: {
    Greet,
  },
  data() {
    return {
      name: "Thanh Dat",
      heroName: "Dat Crazy Dog",
    };
  },
};
</script>

<style scoped></style>
