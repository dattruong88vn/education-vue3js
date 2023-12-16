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
  <br />
  <div>
    <h2>Binding Attribute</h2>
    <h4 v-bind:id="headingId">Heading 4 Text</h4>
    <div v-bind:class="wrapperClass">
      <div v-bind:class="itemClass">1</div>
      <div v-bind:class="itemClass">2</div>
      <div class="p-md">3</div>
    </div>
    <input v-bind:disabled="isDisabled" placeholder="name" />
  </div>
  <br />
  <div>
    <h2>Binding class</h2>
    <div v-bind:class="isPromotion ? 'promoted' : 'not-promoted'">
      v-bind:class with condition
    </div>
    <div
      v-bind:class="{
        'not-promoted': true,
        'p-md': true,
      }"
    >
      v-bind:class with object
    </div>
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
      headingId: "heading-4-id",
      wrapperClass: "flex justify-center items-center",
      itemClass: "p-md",
      isDisabled: true,
      isPromotion: true,
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

.flex {
  display: flex;
}

.justify-center {
  justify-content: center;
}

.items-center {
  align-items: center;
}

.p-md {
  padding: 0.5rem;
  border: 1px solid red;
}

.promoted {
  color: green;
  font-weight: bold;
}

.not-promoted {
  color: red;
  font-weight: lighter;
}
</style>
