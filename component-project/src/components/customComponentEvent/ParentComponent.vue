<template>
  <div>
    <button @click="handleClosePopup(true)">Open popup</button>
    <div v-show="showPopup">
      <Popup @closePopup="handleClosePopup" />
    </div>
  </div>
</template>

<script>
import Popup from "./PopupComponent.vue";

export default {
  name: "Parent-Comp",
  data() {
    return {
      showPopup: false,
    };
  },
  methods: {
    handleClosePopup(value) {
      this.showPopup = value;
    },
  },
  components: {
    Popup,
  },
};
</script>

<style scoped></style>
