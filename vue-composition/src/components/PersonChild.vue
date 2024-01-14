<template>
  <div>Composition Prop computed: Hello {{ cFullName }}</div>
  <button @click="handleEmitCustomEvent">Click</button>
</template>

<script>
import { computed } from "vue";

export default {
  name: "Person-Child",
  props: {
    firstName: {
      type: String,
    },
    lastName: {
      type: String,
    },
  },
  setup(props, context) {
    const cFullName = computed(() => {
      return `${props.firstName} ${props.lastName}`;
    });

    function handleEmitCustomEvent() {
      console.log({ context, cFullName });
      context.emit("customEventName", cFullName.value);
    }

    return {
      cFullName,
      handleEmitCustomEvent,
    };
  },
  emits: ["customEventName"],
};
</script>

<style scoped></style>
