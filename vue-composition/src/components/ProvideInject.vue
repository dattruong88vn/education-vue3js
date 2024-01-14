<template>
  <h2>Parent Component Provide: {{ name }}</h2>
  <h3>Parent Component Provide composition: {{ cUserName }}</h3>

  <h3>Parent Component Provide composition ref: {{ count }}</h3>
  <h3>
    Parent Component Provide composition reactive: {{ firstName }}
    {{ lastName }}
  </h3>
  <button @click="increamentCount">Click</button>
  <ChildA />
</template>

<script>
import { provide, ref, reactive, toRefs } from "vue";

import ChildA from "./ChildA.vue";

export default {
  name: "Provide-Inject",
  components: {
    ChildA,
  },
  setup() {
    const cUserName = ref("Dat 09");
    const count = ref(0);
    function increamentCount() {
      count.value++;
    }

    const state = reactive({
      firstName: "Clark",
      lastName: "Kent",
    });

    provide("c_userName", cUserName);
    provide("c_count", count);
    provide("c_state", state);
    provide("c_click", increamentCount);

    return {
      cUserName,
      count,
      ...toRefs(state),
      increamentCount,
    };
  },
  data() {
    return {
      name: "Thanh Dat",
    };
  },
  provide() {
    return {
      username: this.name,
    };
  },
};
</script>

<style scoped></style>
