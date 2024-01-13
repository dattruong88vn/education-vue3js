<template>
  <div class="section">
    <input type="text" placeholder="First Name" v-model="firstName" />
    <input type="text" placeholder="Last Name" v-model="lastName" />
    <h2>Options API full name is {{ fullName }}</h2>
  </div>
  <hr />
  <div class="section">
    <input type="text" placeholder="First Name" v-model="refFirstName" />
    <input type="text" placeholder="Last Name" v-model="refLastName" />
    <h2>Composition API: ref function full name is {{ refFullName }}</h2>
  </div>
  <hr />
  <div class="section">
    <input type="text" placeholder="First Name" v-model="reactiveFirstName" />
    <input type="text" placeholder="Last Name" v-model="reactiveLastName" />
    <h2>Composition API: ref function full name is {{ reactiveFullName }}</h2>
  </div>
</template>

<script>
import { ref, computed, reactive, toRefs } from "vue";

export default {
  name: "Computed-Composition",
  setup() {
    // ref function
    const refFirstName = ref("");
    const refLastName = ref("");

    const refFullName = computed(() => {
      return `${refFirstName.value} ${refLastName.value}`;
    });

    // reactive function
    const state = reactive({
      reactiveFirstName: "",
      reactiveLastName: "",
    });

    const reactiveFullName = computed(function () {
      return `${state.reactiveFirstName} ${state.reactiveLastName}`;
    });

    return {
      refFirstName,
      refLastName,
      refFullName,
      ...toRefs(state),
      reactiveFullName,
    };
  },
  data() {
    return {
      firstName: "",
      lastName: "",
    };
  },
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    },
  },
};
</script>

<style scoped>
.section {
  padding: 30px;
}
</style>
