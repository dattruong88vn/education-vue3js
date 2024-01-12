<template>
  <div>
    <h2>Binding keys with toRef() function: {{ firstName }} {{ lastName }}</h2>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {
  name: "DemoThree",
  setup() {
    const state = reactive({
      firstName: "Bruce",
      lastName: "Wayne",
    });

    setTimeout(() => {
      state.firstName = "Clark";
      state.lastName = "Kent";
    }, 2000);

    return toRefs(state);
  },
};
</script>

<style scoped></style>
