<template>
  <h2>Popup up</h2>
  <button @click="$emit('closePopup', false)">Close Popup</button>
</template>

<script>
export default {
  name: "Popup-Component",
  emits: ["closePopup"],
};
</script>

<style scoped></style>
