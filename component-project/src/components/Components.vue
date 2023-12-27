<template>
  <Greet name="Bruce" hero-name="Batman" />
  <Greet name="Clark" hero-name="Superman" />
  <Greet id="abc" name="Diana" hero-name="Wonder Woman" />
  <Greet :name="name" :hero-name="heroName" :age="35" :isOld="true" />
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
