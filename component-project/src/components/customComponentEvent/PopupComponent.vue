<template>
  <h2>Popup up</h2>
  <input type="text" v-model="name" />
  <button @click="$emit('closePopup', name)">Close Popup</button>
</template>

<script>
export default {
  name: "Popup-Component",
  emits: {
    closePopup: (name) => {
      return !!name;
    },
  },
  data() {
    return {
      name: "",
    };
  },
};
</script>

<style scoped></style>
