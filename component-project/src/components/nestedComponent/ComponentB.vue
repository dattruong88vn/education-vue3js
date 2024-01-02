<template>
  <ComponentC />
</template>

<script>
import ComponentC from "./ComponentC.vue";

export default {
  name: "ComponentB",
  components: {
    ComponentC,
  },
};
</script>

<style scoped></style>
