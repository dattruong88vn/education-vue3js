<template>
  <h3>Child Component</h3>
</template>

<script>
export default {
  name: "Child-Component",
  beforeCreate() {
    console.log("Child Before Create");
  },
  created() {
    console.log("Child created");
  },
  beforeMount() {
    console.log("Child Before Mount");
  },
  mounted() {
    console.log("Child mounted");
  },
  beforeUpdate() {
    console.log("Child Before Update");
  },
  updated() {
    console.log("Child updated");
  },
  beforeUnmount() {
    console.log("Child Before Unmount");
  },
  unmounted() {
    console.log("Child unmounted");
  },
};
</script>

<style scoped></style>
