<template>
  <!-- <Binding /> -->
  <!-- <ConditionalRendering /> -->
  <!-- <ListRendering /> -->
  <!-- <MethodEvent /> -->
  <!-- <HandleEvent /> -->
  <!-- <FormHandling /> -->
  <!-- <BonusDirective /> -->
  <!-- <ComputedProperties /> -->
  <WatchersData />
</template>

<script>
// import Binding from "./components/Binding.vue";
// import ConditionalRendering from "./components/ConditionalRendering.vue";
// import ListRendering from "./components/ListRendering.vue";
// import MethodEvent from "./components/MethodEvent.vue";
// import HandleEvent from "./components/HandleEvent.vue";
// import FormHandling from "./components/FormHandling.vue";
// import BonusDirective from "./components/Bonus-directive.vue";
// import ComputedProperties from "./components/ComputedProperties.vue";
import WatchersData from "./components/WatchersData.vue";

export default {
  name: "App",
  components: {
    // Binding,
    // ConditionalRendering,
    // ListRendering,
    // MethodEvent,
    // HandleEvent,
    // FormHandling,
    // BonusDirective,
    // ComputedProperties,
    WatchersData,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
