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
    <h4 v-bind:class="isPromotion ? 'promoted' : 'not-promoted'">
      v-bind:class with condition
    </h4>
    <h4
      v-bind:class="{
        'not-promoted': true,
        'p-md': true,
      }"
    >
      v-bind:class with object
    </h4>
  </div>
  <br />
  <div>
    <h2>Binding Style</h2>
    <h4
      v-bind:style="{
        color: hightlightColor,
        fontWeight: hightlightWeight,
        'font-size': hightlightSize,
      }"
    >
      Object
    </h4>
    <h4 v-bind:style="hightlightObject">Object 2</h4>
    <h4 v-bind:style="[baseStyleObject, successStyleObject]">Array</h4>
    <h4 v-bind:style="[baseStyleObject, dangerStyleObject]">Array</h4>
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
      // style
      hightlightColor: "red",
      hightlightWeight: "bold",
      hightlightSize: "20px",
      hightlightObject: {
        color: "orange",
        fontSize: "30px",
        fontWeight: "bold",
      },
      baseStyleObject: {
        color: "purple",
        fontSize: "20px",
      },
      successStyleObject: {
        backgroundColor: "green",
        border: "1px solid red",
      },
      dangerStyleObject: {
        backgroundColor: "red",
        border: "1px solid green",
      },
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
