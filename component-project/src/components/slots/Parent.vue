<template>
  <Children />
  <Children> Text only </Children>
  <Children> <h2>Text in h2 element</h2></Children>
  <Children>
    <img src="https://picsum.photos/200" />
  </Children>
</template>

<script>
import Children from "./Children.vue";
export default {
  name: "slot-parent",
  components: {
    Children,
  },
};
</script>

<style scoped></style>
