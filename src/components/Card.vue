<template>
  <div class="m-card">
    <h2 class="m-card__header">{{movie.Title}}</h2>

    <img class="m-card__image" :src="movie.Poster" alt="movie poster" />

    <p class="m-card__paragraph">{{movie.Plot}}</p>
  </div>
</template>

<script>
export default {
  props: ["movie"]
};
</script>

<style>
</style>