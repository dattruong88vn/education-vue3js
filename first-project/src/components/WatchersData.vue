<template>
  <h1>Watchers</h1>
  <div>
    <h2>Volume Trackers (0 - 20)</h2>
    <h3>Current Volume: {{ volume }}</h3>
    <div>
      <button @click="volume -= 2">Decrease</button>
      <button @click="volume += 2">Increase</button>
    </div>
  </div>
  <div>
    <input type="text" v-model="name" />
  </div>
</template>

<script>
export default {
  name: "WatchersData",
  data() {
    return {
      volume: 0,
      name: "",
    };
  },
  methods: {},
  computed: {
    nameAndVolume() {
      return { name: this.name, volume: this.volume };
    },
  },
  watch: {
    volume(newVolume, oldVolume) {
      if (newVolume > oldVolume && newVolume === 16) {
        alert("High volume may damage your hearing");
      }
    },
    name(newName) {
      if (newName === "DAT") {
        alert("Hi superhero");
      }
    },
    nameAndVolume(newData, oldData) {
      if (
        newData.volume > oldData.volume &&
        newData.volume === 18 &&
        newData.name === "DAT"
      ) {
        alert("Watchers multidata");
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
