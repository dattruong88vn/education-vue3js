<template>
  <Children>
    <template v-slot:header> Header </template>
    <template v-slot:default>
      <img src="https://picsum.photos/200" />
    </template>
    <template v-slot:footer> Footer </template>
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
