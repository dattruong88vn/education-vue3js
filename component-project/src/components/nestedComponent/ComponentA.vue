<template>
  <ComponentB />
</template>

<script>
import ComponentB from "./ComponentB.vue";

export default {
  name: "ComponentA",
  components: {
    ComponentB,
  },
};
</script>

<style scoped></style>
