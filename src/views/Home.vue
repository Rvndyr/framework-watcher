<template>
  <div>
    <div>
      <b-jumbotron bg-variant="secondary" text-variant="white">
        <template #header>JS Framework Watcher</template>

        <template #lead>
          A simple table that allows you to see how frequent some Javascript frameworks are used.
        </template>

        <hr class="my-4" />

        <p>Utilizing the Github Api, we are fetching information from React, Svelte, Vue, and Angular.</p>
      </b-jumbotron>
    </div>
    <b-container v-if="repos.length === 5">
      <table class="table table-dark">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">
              Repos
              <img src="https://img.icons8.com/color/48/000000/github--v1.png" />
            </th>
            <th scope="col">
              Starred
              <img src="https://img.icons8.com/color/48/000000/filled-star--v1.png" />
            </th>
            <th scope="col">
              Forked
              <img src="https://img.icons8.com/color/48/000000/code-fork--v1.png" />
            </th>
            <th scope="col">
              Watchers
              <img src="https://img.icons8.com/color/48/000000/visible--v1.png" />
            </th>
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
    <hr />

    <div></div>
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
