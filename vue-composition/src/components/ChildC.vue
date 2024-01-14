<template>
  <h2>ChildC Component inject: {{ username }}</h2>
  <h3>ChildC Component composition inject: {{ cUserName }}</h3>

  <h3>ChildC Component Provide composition ref: {{ cCount }}</h3>
  <h3>
    ChildC Component Provide composition reactive: {{ firstName }}
    {{ lastName }}
  </h3>
  <button @click="cIncrementCount">Click</button>
</template>

<script>
import { inject, toRefs } from "vue";

export default {
  name: "ChildC",
  setup() {
    const cUserName = inject("c_userName", "Default User Name");

    const cCount = inject("c_count", 0);
    const cState = inject("c_state", {});
    const cIncrementCount = inject("c_click", () => {});

    return {
      cUserName,
      cCount,
      ...toRefs(cState),
      cIncrementCount,
    };
  },
  inject: ["username"],
};
</script>

<style lang="scss" scoped></style>
