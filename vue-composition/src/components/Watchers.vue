<template>
  <div>
    <h2>Options</h2>
    <input type="text" placeholder="name" v-model="name" />
  </div>
  <hr />
  <div>
    <h2>Composition: ref</h2>
    <input type="text" placeholder="first name" v-model="firstName" />
    <input type="text" placeholder="last name" v-model="lastName" />
  </div>
  <hr />
  <div>
    <h2>Composition: reactive</h2>
    <input type="text" placeholder="first name" v-model="reactiveFirstName" />
    <input type="text" placeholder="last name" v-model="reactiveLastName" />
    <input type="text" placeholder="hero name" v-model="options.heroName" />
  </div>
</template>

<script>
import { ref, watch, reactive, toRefs } from "vue";
import _ from "lodash";

export default {
  name: "Watchers-Composition",
  setup() {
    const firstName = ref("");
    const lastName = ref("");

    // watch single data
    watch(firstName, (newVal, oldval) => {
      console.log("composition old value: ", oldval);
      console.log("composition new value: ", newVal);
    });

    // watch multiple data
    watch(
      [firstName, lastName],
      (newVals, oldVals) => {
        console.log("Old First name: ", oldVals[0]);
        console.log("Old Last name: ", oldVals[1]);
        console.log("new First name: ", newVals[0]);
        console.log("new Last name: ", newVals[1]);
      },
      { immediate: true }
    );

    // reactive
    const state = reactive({
      reactiveFirstName: "",
      reactiveLastName: "",
      options: {
        heroName: "",
      },
    });

    watch(
      () => {
        return _.cloneDeep(state);
      },
      (newVal, oldVal) => {
        console.log("Old:", oldVal);
        console.log("New:", newVal);
      }
    );

    // watch(
    //   () => {
    //     return { ...state.options };
    //   },
    //   (newValue, oldValue) => {
    //     console.log("reactive state option new", newValue);
    //     console.log("reactive state option old", oldValue);
    //   },
    //   { deep: true }
    // );

    return { firstName, lastName, ...toRefs(state) };
  },
  data() {
    return {
      name: "",
    };
  },
  watch: {
    name(newVal, oldVal) {
      console.log("options old value: ", oldVal);
      console.log("options new value: ", newVal);
    },
  },
};
</script>

<style lang="scss" scoped></style>
