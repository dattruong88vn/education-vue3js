<template>
  <h2>Name use variable: {{ name }}</h2>
  <h2>Name2 use ref function: {{ name2 }}</h2>
</template>

<script>
import { ref } from "vue";

export default {
  name: "DemoOne",
  setup() {
    let name = "Bruce";
    const name2 = ref("Bruce");

    setTimeout(() => {
      name = "Clark";
      name2.value = "Clark";
      console.log({ name, name2: name2.value });
    }, 2000);

    return {
      name,
      name2,
    };
  },
};
</script>

<style scoped></style>
