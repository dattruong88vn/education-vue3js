<template>
  <div>
    <h2>Binding Object: {{ state.firstName }} {{ state.lastName }}</h2>
    <h2>Binding keys: {{ firstName }} {{ lastName }}</h2>
  </div>
</template>

<script>
import { reactive } from "vue";

export default {
  name: "DemoTwo",
  setup() {
    const state = reactive({
      firstName: "Bruce",
      lastName: "Wayne",
    });

    setTimeout(() => {
      state.firstName = "Clark";
      state.lastName = "Kent";
    }, 2000);

    return {
      state,
      firstName: state.firstName,
      lastName: state.lastName,
    };
  },
};
</script>

<style scoped></style>
