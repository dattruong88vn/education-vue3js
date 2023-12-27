<template>
  <div>
    <h2 v-bind="$attrs">
      Hello {{ name }} a.k.a {{ heroName }} has {{ age }} and is
      {{ isOld ? "old" : "young" }}
    </h2>
  </div>
</template>

<script>
export default {
  name: "greet-component",
  props: {
    name: String,
    heroName: String,
    age: {
      type: Number,
      default: 20,
    },
    isOld: {
      type: Boolean,
      default: false,
    },
  },
  inheritAttrs: false,
};
</script>

<style scoped></style>
