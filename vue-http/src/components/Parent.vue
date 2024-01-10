<template>
  <div>
    <h2>Parent Component</h2>
    <button @click="showChild = !showChild">Toggle Child</button>
    <template v-if="showChild">
      <Child />
    </template>
  </div>
</template>

<script>
import Child from "./Child.vue";

export default {
  name: "Parent-Component",
  components: {
    Child,
  },
  data() {
    return {
      showChild: true,
    };
  },
  beforeCreate() {
    console.log("Parent Before Create");
  },
  created() {
    console.log("Parent created");
  },
  beforeMount() {
    console.log("Parent Before Mount");
  },
  mounted() {
    console.log("Parent mounted");
  },
  beforeUpdate() {
    console.log("Parent Before Update");
  },
  updated() {
    console.log("Parent updated");
  },
  beforeUnmount() {
    console.log("Parent Before Unmount");
  },
  unmounted() {
    console.log("Parent unmounted");
  },
};
</script>

<style scoped></style>
