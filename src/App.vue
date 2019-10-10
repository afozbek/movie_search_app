<template>
  <div>
    <div class="m-search">
      <input
        class="m-search__input"
        v-model="title"
        type="text"
        placeholder="Search Any Movie or Series"
      />
      <button class="m-search__button" @click="getMovie">Find Your Movie</button>
    </div>

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

.m-search {
  @include flex(column, wrap, center);

  &__input {
    width: 90%;
    height: 50px;

    margin: 0 auto;
    border: 3px solid red;

    &::placeholder {
      text-align: center;
    }
  }
}

</style>
