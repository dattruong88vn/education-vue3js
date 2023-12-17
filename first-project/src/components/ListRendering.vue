<template>
  <h1>List Rendering</h1>
  <div>
    <h2>Array of string</h2>
    <h4 v-for="(name, index) in names" v-bind:key="name">
      {{ index + 1 }} {{ name }}
    </h4>
  </div>

  <div>
    <h2>Array of Object</h2>
    <h4 v-for="(fullName, index) in fullNames" :key="fullName.id">
      {{ index + 1 }} {{ fullName.fName }} - {{ fullName.lName }}
    </h4>
  </div>

  <div>
    <h2>Array of Array</h2>
    <h4 v-for="actor in actors" :key="actor.id">
      <h6>{{ actor.name }}</h6>
      <span v-for="movie in actor.movies" :key="movie">{{ movie }}</span>
    </h4>
  </div>

  <div>
    <h2>Loop an Object</h2>
    <h4 v-for="(value, key, index) of myInfo" :key="key">
      {{ index + 1 }} {{ key }}:{{ value }}
    </h4>
  </div>

  <div>
    <h2>Loop an Object with template tag</h2>
    <template v-for="(value, key, index) of myInfo" :key="key">
      <span>{{ index + 1 }}</span>
      <span>{{ key }}</span>
      <span>{{ value }}</span>
    </template>
  </div>

  <div>
    <h2>Conditional List Rendering</h2>
    <template v-for="name in names" :key="name">
      <h4 v-if="name === 'Batman'">{{ name }}</h4>
    </template>
  </div>
</template>

<script>
export default {
  data() {
    return {
      names: ["Batman", "Superman", "The Flash"],
      fullNames: [
        { id: 1, fName: "Bruce", lName: "Wayne" },
        { id: 2, fName: "Clark", lName: "Kent" },
        { id: 3, fName: "Barry", lName: "Allen" },
      ],
      actors: [
        { id: 1, name: "Batman", movies: [1, 2, 3] },
        { id: 2, name: "Superman", movies: [4, 5, 6] },
        { id: 3, name: "The Flash", movies: [7, 8, 9] },
      ],
      myInfo: {
        name: "Thanh Dat",
        age: 35,
        job: "Software Developer",
      },
    };
  },
};
</script>

<style lang="scss" scoped></style>
