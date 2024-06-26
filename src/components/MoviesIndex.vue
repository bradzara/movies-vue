<script>
export default {
  props: {
    movies: Array,
  },
};
</script>

<template>
  <div>
    <h1>All Movies</h1>

    <div v-for="movie in movies" v-bind:key="movie.id">
      <h2> {{ movie.name }}</h2>
      <img v-bind:src="movie.image_url" class="resized-image" />
      <p>Released: {{ movie.release_year }}</p>
      <p>Run Time: {{ movie.run_time }} minutes</p>
      <hr>
    </div>
  </div>
</template>

<style></style>