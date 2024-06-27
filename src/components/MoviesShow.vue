<script>
export default {
  props: {
    movie: Object,
  },
};
</script>

<!-- <template>
  <div>
    <h1>Movie information</h1>
    <p>Name: {{ movie.name }}</p>
    <p>Movie Poster: <img :src="movie.image_url" alt="Movie Image" /></p>
    <p>Released: {{ movie.release_year }}</p>
    <p>Run Time: {{ movie.run_time }}</p>
  </div>
</template>

<style></style> -->

<template>
  <div>
    <h1 class="modal-title">Movie Information</h1>
    <p class="modal-text">Name: {{ movie.name }}</p>
    <p class="modal-text">Image: <img :src="movie.image_url" alt="Movie Image" /></p>
    <p class="modal-text">Released: {{ movie.release_year }}</p>
    <p class="modal-text">Run Time: {{ movie.run_time }}</p>
  </div>
</template>

<style>
.modal-title {
  font-size: 24px; /* Adjust the size as needed */
}

.modal-text {
  font-size: 18px; /* Adjust the size as needed */
}

#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
}

button:hover {
  background-color: #45a049;
}
</style>



