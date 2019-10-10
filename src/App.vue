<template>
  <div class="m-container">
    <app-card v-if="searched" :movie="movie"></app-card>
  </div>
</template>

<script>
import axios from "axios";

import Card from "./components/Card.vue";

export default {
  name: "App",
  data() {
    return {
      movie: [],
      searched: false,
      title: "",
      apiKey: process.env.VUE_APP_APIKEY
    };
  },
  components: {
    appCard: Card
  },
  methods: {
    async getMovie() {
      const movie = await axios.get(
        `http://www.omdbapi.com/?t=${this.title}&apikey=${this.apiKey}`
      );

      this.searched = true;
      this.movie = movie.data;
    }
  }
};
</script>

<style lang="scss">
@import "./scss/main.scss";

</style>
