<template>
  <div class="home">
    <b-container>
      <table class="table table-dark">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">Repo</th>
            <th scope="col">Starred</th>
            <th scope="col">Forked</th>
            <th scope="col">Watchers</th>
            <th scope="col">Popularity</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">1</th>
            <td>{{ this.repos[0].name }}</td>
            <td>{{ this.repos[0].stargazers_count }}</td>
            <td>{{ this.repos[0].forks }}</td>
            <td>{{ this.repos[0].watchers_count }}</td>
          </tr>
          <tr>
            <th scope="row">2</th>
            <td>{{ this.repos[1].name }}</td>
            <td>{{ this.repos[1].stargazers_count }}</td>
            <td>{{ this.repos[1].forks }}</td>
            <td>{{ this.repos[1].watchers_count }}</td>
          </tr>
          <tr>
            <th scope="row">3</th>
            <td>{{ this.repos[2].name }}</td>
            <td>{{ this.repos[2].stargazers_count }}</td>
            <td>{{ this.repos[2].forks }}</td>
            <td>{{ this.repos[2].watchers_count }}</td>
          </tr>
          <tr>
            <th scope="row">4</th>
            <td>{{ this.repos[3].name }}</td>
            <td>{{ this.repos[3].stargazers_count }}</td>
            <td>{{ this.repos[3].forks }}</td>
            <td>{{ this.repos[3].watchers_count }}</td>
          </tr>
        </tbody>
      </table>
    </b-container>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      repos: [],
    };
  },
  created: function () {
    axios.get("https://api.github.com/repos/vuejs/vue").then((response) => {
      this.repos[0] = response.data;
      console.log(this.repos[0]);
    });
    axios.get("https://api.github.com/repos/angular/angular.js").then((response) => {
      this.repos[1] = response.data;
      console.log(this.repos[1]);
    });
    axios.get("https://api.github.com/repos/emberjs/ember.js").then((response) => {
      this.repos[2] = response.data;
      console.log(this.repos[2]);
    });
    axios.get("https://api.github.com/repos/sveltejs/svelte").then((response) => {
      this.repos[3] = response.data;
      console.log(this.repos[3]);
    });
    axios.get("https://api.github.com/repos/facebook/react").then((response) => {
      this.repos[4] = response.data;
      console.log(this.repos[4]);
    });
  },
  methods: {},
};
</script>
