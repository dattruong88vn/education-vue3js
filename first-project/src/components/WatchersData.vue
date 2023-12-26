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
    <h2>Watch whan has changed</h2>
    <label>Name</label>
    <input type="text" v-model="name" />
  </div>
  <div>
    <h2>Watch immidiate</h2>
    <label>Movie</label>
    <input type="text" v-model="movie" />
  </div>
  <div>
    <h2>Watch deep inside object</h2>
    <div>
      <label>Title</label>
      <input type="text" v-model="movieInfo.title" />
    </div>
    <div>
      <label>Author</label>
      <input type="text" v-model="movieInfo.author" />
    </div>
  </div>
  <div>
    <button @click="movieList.push('Wonder Woman')">Add movie</button>
  </div>
</template>

<script>
export default {
  name: "WatchersData",
  data() {
    return {
      volume: 0,
      name: "",
      movie: "Thanh Dat",
      timeOut: null,
      movieInfo: {
        author: "",
        title: "",
      },
      movieList: ["Batman", "Superman"],
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
    movie: {
      handler(newMovie) {
        if (this.timeOut) clearTimeout(this.timeOut);

        this.timeOut = setTimeout(() => {
          console.log(`Call api with movie name ${newMovie}`);
        }, 1000);
      },
      immediate: true,
    },
    movieInfo: {
      handler(newData) {
        console.log(
          `Change data inside object ${newData.title} and ${newData.author}`
        );
      },
      deep: true,
    },
    movieList: {
      handler(newList) {
        console.log(`Call api with list ${newList}`);
      },
      deep: true,
    },
    beforeDestroy() {
      clearTimeout(this.timeOut);
    },
  },
};
</script>

<style lang="scss" scoped></style>
