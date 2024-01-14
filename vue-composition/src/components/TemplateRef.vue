<template>
  <div>
    <input type="text" ref="inputRef" />
  </div>
</template>

<script>
import { onMounted, ref } from "vue";

export default {
  name: "TemplateRef",
  setup() {
    const inputRef = ref(null);

    // composition api
    onMounted(() => {
      inputRef.value.focus();
    });

    return {
      inputRef,
    };
  },
  //   options api
  //   mounted() {
  //     this.$refs.inpurRef.focus();
  //   },
};
</script>

<style scoped></style>
