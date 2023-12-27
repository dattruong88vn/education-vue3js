<template>
  <div>
    <h2>Hello {{ name }} a.k.a {{ heroName }}</h2>
  </div>
</template>

<script>
export default {
  name: "greet-component",
  props: {
    name: String,
    heroName: String,
  },
};
</script>

<style scoped></style>
