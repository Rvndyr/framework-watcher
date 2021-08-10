<template>
  <div class="Home">
    <div>{{ repos.length }}</div>
    <div v-if="repos.length === 5">
      <table class="table table-dark">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">Repos</th>
            <th scope="col">Starred</th>
            <th scope="col">Forked</th>
            <th scope="col">Watchers</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(repo, key) in repos" :key="key">
            <th scope="row">{{ key + 1 }}</th>
            <td>{{ repo.name }}</td>
            <td>{{ repo.stargazers_count }}</td>
            <td>{{ repo.forks }}</td>
            <td>{{ repo.watchers_count }}</td>
          </tr>
          <!-- <tr>
            <th scope="row">2</th>
            <td>{{ repos[1].name }}</td>
            <td>{{ repos[1].stargazers_count }}</td>
            <td>{{ repos[1].forks }}</td>
            <td>{{ repos[1].watchers_count }}</td>
          </tr>
          <tr>
            <th scope="row">3</th>
            <td>{{ repos[2].name }}</td>
            <td>{{ repos[2].stargazers_count }}</td>
            <td>{{ repos[2].forks }}</td>
            <td>{{ repos[2].watchers_count }}</td>
          </tr>
          <tr>
            <th scope="row">4</th>
            <td>{{ repos[3].name }}</td>
            <td>{{ repos[3].stargazers_count }}</td>
            <td>{{ repos[3].forks }}</td>
            <td>{{ repos[3].watchers_count }}</td>
          </tr>
          <tr>
            <th scope="row">5</th>
            <td>{{ repos[4].name }}</td>
            <td>{{ repos[4].stargazers_count }}</td>
            <td>{{ repos[4].forks }}</td>
            <td>{{ repos[4].watchers_count }}</td>
          </tr> -->
        </tbody>
      </table>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data() {
    return {
      repos: [],
    };
  },
  mounted() {
    this.LoadData();
  },
  methods: {
    LoadData() {
      axios.get("https://api.github.com/repos/vuejs/vue").then((response) => {
        this.repos.push(response.data);
        console.log(this.repos[0]);
      });
      axios.get("https://api.github.com/repos/angular/angular.js").then((response) => {
        this.repos.push(response.data);
        console.log(this.repos[1]);
      });
      axios.get("https://api.github.com/repos/emberjs/ember.js").then((response) => {
        this.repos.push(response.data);
        console.log(this.repos[2]);
      });
      axios.get("https://api.github.com/repos/sveltejs/svelte").then((response) => {
        this.repos.push(response.data);
        console.log(this.repos[3]);
      });
      axios.get("https://api.github.com/repos/facebook/react").then((response) => {
        this.repos.push(response.data);
        console.log(this.repos[4]);
      });
    },
  },
};
</script>
