<template>
  <div class="home">
    <h1>{{ message }}</h1>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      repo: null,
    };
  },
  created: function () {
    axios.get("https://api.github.com/repos/vuejs/vue").then((response) => {
      console.log(response);
      this.repo = response.data;
      console.log("This is the data:", this.repo);
    });
  },
  methods: {},
};
</script>
