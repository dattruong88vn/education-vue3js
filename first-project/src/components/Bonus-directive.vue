<template>
  <div>
    <div v-once>{{ name }}</div>
    <button @click="name = 'Dat Crazy Dog'">Change Name</button>
    <div v-pre>{{ name }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Thanh Dat",
    };
  },
};
</script>

<style lang="scss" scoped></style>
