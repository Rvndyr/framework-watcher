<template>
  <div class="Home">
    <b-container v-if="repos.length === 5">
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
        </tbody>
      </table>
    </b-container>
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
      let repoUrl = ["vuejs/vue", "emberjs/ember.js", "sveltejs/svelte", "facebook/react", "angular/angular"];
      repoUrl.forEach((url) => {
        axios.get(`https://api.github.com/repos/${url}`).then((response) => {
          console.log(response.data);
          this.repos.push(response.data);
          console.log(this.repos);
        });
      });
    },
  },
};
</script>
