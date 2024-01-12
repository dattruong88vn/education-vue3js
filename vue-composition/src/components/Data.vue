<template>
  <div>
    <h2>Options - {{ o_firstName }}</h2>
    <h2>Composition - {{ c_firstName }}</h2>
    <h2>Composition with computed - {{ greet }}</h2>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "DataComposition",
  setup() {
    const c_firstName = ref("Dat 09");
    c_firstName.value = `${c_firstName.value}0909`;
    const greet = `Hello ${c_firstName.value}`;
    return {
      c_firstName,
      greet,
    };
  },
  data() {
    return {
      o_firstName: "Thanh Dat",
    };
  },
};
</script>

<style scoped></style>
