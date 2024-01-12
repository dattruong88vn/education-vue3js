<template>
  <div>
    <h2>Name: {{ name }}</h2>
    <button @click="changeNameOption">Change name with option API</button>
  </div>
  <hr />
  <div>
    <h2>Count (ref function): {{ count }}</h2>
    <button @click="increaseCount">Increase Count with Composition API</button>
  </div>
  <hr />
  <div>
    <h2>
      Full Name (reactive and toRefs function): {{ firstName }} - {{ lastName }}
    </h2>
    <button @click="updateName">Update Name with Composition API</button>
  </div>
</template>

<script>
import { ref, reactive, toRefs } from "vue";

export default {
  name: "MethodComposition",
  setup() {
    const count = ref(0);
    const state = reactive({
      firstName: "Bruce",
      lastName: "Wayne",
    });

    const increaseCount = () => {
      count.value++;
    };

    const updateName = () => {
      state.firstName = "Clark";
      state.lastName = "Kent";
    };

    return {
      count,
      increaseCount,
      ...toRefs(state),
      updateName,
    };
  },
  data() {
    return {
      name: "Bruce",
    };
  },
  methods: {
    changeNameOption() {
      this.name = "Batman";
    },
  },
};
</script>

<style scoped></style>
