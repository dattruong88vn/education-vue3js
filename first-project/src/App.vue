<template>
  <div>
    <h2>Binding Text</h2>
    <div>Name: {{ name }}</div>
    <div>Age: {{ age }}</div>
    <div v-text="channel"></div>
  </div>
  <br />
  <div>
    <h2>Binding html</h2>
    <div>{{ channelHtml }}</div>
    <div v-html="channelHtml"></div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "Thanh Dat",
      age: 35,
      channel: "dattruong88vn",
      channelHtml: "<b>Binding Html</b>",
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
