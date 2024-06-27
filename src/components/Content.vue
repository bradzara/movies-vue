<script>
import axios from "axios";
import MoviesIndex from "./MoviesIndex.vue";
import backgroundImage from "/Users/bradleyzara/Desktop/unnamed.png";

export default {
  components: {
    MoviesIndex,
  },

  data: function () {
      return {
        movies: [],
        randomMovie: null,
        backgroundImage: backgroundImage,
      };
    },

  created: function () {
    this.handleIndexMovies();
  },
  methods: {
    handleIndexMovies: function () {
      axios.get("http://127.0.0.1:5000/movies.json").then((response) => {
        console.log("movies index", response);
        this.movies = response.data;
      });
    },

    generateRandomMovie: function () {
      if (this.movies.length === 0 ) {
        console.warn("No movies available to choose from.");
        return;
      }
      const randomIndex = Math.floor(Math.random() * this.movies.length);
      this.randomMovie = this.movies[randomIndex];
    }
  },
};

</script>

<template>
  <div id="app">
    <h1>Random Movie Generator</h1>
    <button @click="generateRandomMovie">Generate Random Movie</button>
    <div v-if="randomMovie" class="movie-card" > 
      <h3>{{ randomMovie.name }}</h3>
      <img :src="randomMovie.image_url" alt="Movie poster" class="resized-image">
      <p>Release Year: {{ randomMovie.release_year }}</p>
      <p>Genre: {{ randomMovie.genre_id }}</p>
      <p>Run Time: {{ randomMovie.run_time }} minutes</p>
      <p>Reviews: {{ randomMovie.review_id }}</p>
    </div>
    <div v-if="!randomMovie" class="movies-index">
      <MoviesIndex :movies="movies" />
    </div>
  </div>
</template>

<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  overflow-x: hidden;
}


#app {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  text-align: center;
  margin-top: 0;
  padding: 0;
  background: url(/Users/bradleyzara/Desktop/unnamed.png) no-repeat fixed;
  background-size: cover;
  color: #333;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}

h1 {
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 2.5rem;
  color: #ffffff;
  margin-bottom: 20px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  transition: background-color 0.3s, transform 0.3s;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

button:hover {
  background-color: #45a049;
  transform: translateY(-5px);
}

.image-container {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.resized-image {
  width: 300px;
  height: auto;
  margin: 10px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.movies-index {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
  width: 100%;
  max-width: 1200px;
  margin-top: 20px;
}

.movie-card {
  background: rgba(0, 0, 0, 0.465);
  color: #ffffff;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  margin: 10px;
  padding: 15px;
  text-align: center;
  max-width: 400px;
  transition: transform 0.3s;
}

.movie-card:hover {
  transform: translateY(-2px);
}

</style>