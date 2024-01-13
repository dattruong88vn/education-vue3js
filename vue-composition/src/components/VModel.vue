<template>
  <div>
    <h2>Options API</h2>
    <input type="text" placeholder="First Name" v-model="fName" />
    <input type="text" placeholder="Last Name" v-model="lName" />
    <button @click="updateFirstName('Dat 09')">Click</button>
  </div>
  <div>
    <h2>Composition API</h2>
    <input type="text" placeholder="Hero Name" v-model="heroName" />
    <input type="text" placeholder="First Name" v-model="firstName" />
    <input type="text" placeholder="Last Name" v-model="lastName" />
    <button @click="updateFirstNameInSetup('Dat Crazy Dog')">Click</button>
  </div>
</template>

<script>
import { ref, reactive, toRefs } from "vue";

export default {
  name: "VModel",
  methods: {
    updateFirstName(value) {
      this.fName = value;
    },
  },
  setup() {
    const heroName = ref("");
    const stateName = reactive({
      firstName: "",
      lastName: "",
    });

    function updateFirstNameInSetup(value) {
      stateName.firstName = value;
    }

    return {
      heroName,
      ...toRefs(stateName),
      updateFirstNameInSetup,
    };
  },
  data() {
    return {
      fName: "",
      lName: "",
    };
  },
};
</script>

<style scoped></style>
