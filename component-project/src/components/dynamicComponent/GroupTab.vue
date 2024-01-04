<template>
  <div>
    <button v-for="tab in tabTitles" :key="tab" @click="tabActive = tab">
      {{ tab }}
    </button>
  </div>
  <div>
    <TabA v-if="tabActive === 'TabA'" />
    <TabB v-if="tabActive === 'TabB'" />
    <TabC v-if="tabActive === 'TabC'" />
  </div>

  <!-- dynamic component -->
  <component :is="tabActive" />
</template>

<script>
import TabA from "./TabA.vue";
import TabB from "./TabB.vue";
import TabC from "./TabC.vue";
export default {
  name: "group-tab",
  components: {
    TabA,
    TabB,
    TabC,
  },
  data() {
    return {
      tabActive: "TabA",
      tabTitles: ["TabA", "TabB", "TabC"],
    };
  },
};
</script>

<style scoped></style>
