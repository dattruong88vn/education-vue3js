<template>
  <div>
    <input type="text" placeholder="First Name" v-model="cFirstName" />
    <input type="text" placeholder="Last Name" v-model="cLastName" />
    <br />
    <PersonChild
      :firstName="cFirstName"
      :lastName="cLastName"
      @customEventName="handleCustomEventFromChild"
    />
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";
import PersonChild from "./PersonChild.vue";

export default {
  name: "Person-Props",
  components: { PersonChild },
  setup() {
    const profile = reactive({
      cFirstName: "",
      cLastName: "",
    });

    function handleCustomEventFromChild(fullNameChild) {
      alert(`Hey ${fullNameChild}`);
    }

    return {
      ...toRefs(profile),
      handleCustomEventFromChild,
    };
  },
};
</script>

<style scoped></style>
