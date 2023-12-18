<template>
  <div>
    <pre>
        {{ JSON.stringify(formValues, null, 3) }}
    </pre>
  </div>
  <form @submit="submitForm">
    <div>
      <label for="name">Name</label>
      <input id="name" type="text" v-model="formValues.name" />
    </div>

    <div>
      <label for="profile">Profile Summary</label>
      <textarea id="profile" v-model="formValues.profileSummary"></textarea>
    </div>

    <div>
      <label for="country">Country</label>
      <select name="country" v-model="formValues.country">
        <option value="">Select a country</option>
        <option value="india">India</option>
        <option value="vietnam">Vietnam</option>
        <option value="singapore">Singapore</option>
      </select>
    </div>

    <div>
      <label for="job">Job Location</label>
      <select name="job" id="job" multiple v-model="formValues.jobLocation">
        <option value="india">India</option>
        <option value="vietnam">Vietnam</option>
        <option value="singapore">Singapore</option>
      </select>
    </div>

    <div>
      <input
        type="checkbox"
        name="remote"
        id="remote"
        v-model="formValues.remoteWork"
        true-value="yes"
        false-value="no"
      />
      <label for="remote">Open to Remote Work</label>
    </div>

    <div>
      <label>Skills</label>
      <input
        type="checkbox"
        name="html"
        id="html"
        value="html"
        v-model="formValues.skills"
      />
      <label for="html">HTML</label>
      <input
        type="checkbox"
        name="css"
        id="css"
        value="css"
        v-model="formValues.skills"
      />
      <label for="css">CSS</label>
      <input
        type="checkbox"
        name="js"
        id="js"
        value="js"
        v-model="formValues.skills"
      />
      <label for="js">Javascript</label>
    </div>

    <div>
      <label>Years of Experience</label>
      <input
        type="radio"
        id="0-2"
        value="0-2"
        v-model="formValues.yearsOfExp"
      />
      <label for="0-2">0-2</label>
      <input
        type="radio"
        id="2-5"
        value="2-5"
        v-model="formValues.yearsOfExp"
      />
      <label for="2-5">2-5</label>
      <input
        type="radio"
        id="5-10"
        value="5-10"
        v-model="formValues.yearsOfExp"
      />
      <label for="5-10">5-10</label>
    </div>

    <div>
      <button>Submit</button>
    </div>
  </form>
</template>

<script>
import { toRaw } from "vue";
export default {
  data() {
    return {
      formValues: {
        name: "",
        profileSummary: "",
        country: "",
        jobLocation: [],
        remoteWork: "no",
        skills: [],
        yearsOfExp: "",
      },
    };
  },
  methods: {
    submitForm(event) {
      event.preventDefault();
      console.log(toRaw(this.formValues));
    },
  },
};
</script>

<style scoped>
input,
textarea,
select {
  border-radius: 4px;
}
</style>
