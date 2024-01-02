<template>
  <div>Component C data property username: {{ username }}</div>
  <div>Component C computed property datName: {{ datName }}</div>
</template>

<script>
export default {
  name: "ComponentC",
  inject: {
    username: "username",
    datName: "datName",
  },
};
</script>

<style scoped></style>
