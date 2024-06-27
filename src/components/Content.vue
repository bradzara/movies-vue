<script>
import axios from "axios";
import MoviesIndex from "./MoviesIndex.vue";
import MoviesShow from "./MoviesShow.vue";
import Modal from "./Modal.vue";

export default {
  components: {
    MoviesIndex,
    MoviesShow,
    Modal,
  },

  data: function () {
      return {
        movies: [],
        currentMovie: {},
        isMoviesShowVisible: false,
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

    handleShowMovie: function (movie) {
      console.log("handleShowMovie", movie);
      this.currentMovie = movie;
      this.isMoviesShowVisible = true;
    },
    handleClose: function () {
      this.isMoviesShowVisible = false;
    },
  },
};

</script>

<template>
  <div id="app">
    <h1>Random Movie Generator</h1>
    <button @click="generateRandomMovie">Generate Random Movie</button>
    <!-- <p v-if="randomMovie">{{ randomMovie }}</p>  -->
    <!-- WILL USE ABOVE CODE WHEN RANDOMIZER WORKS -->
   <MoviesIndex v-bind:movies="movies" v-on:showMovie="handleShowMovie" />
   <Modal v-bind:show="isMoviesShowVisible" v-on:close="handleClose">
      <MoviesShow v-bind:movie="currentMovie" />
    </Modal>
  </div>
</template>




<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  overflow-x: hidden; /* Prevent horizontal scroll */
}


#app {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  text-align: center;
  margin-top: 0;
  padding: 0;
  background: url('https://lh3.googleusercontent.com/gg/AJIvXiuAOFMdgn2Y5yPfia4wNQxZ6Fx7ZTEDyBYU3jSGBLF_ir6bh-MoJiZ84uxedsPJugYFqj0Mgn5AiMYciyDHc9mrDKeGTZjR4WaAh4_tJ-uEYLlfJJ4JmWeIHse37wyMgqzZY5NcMCzajfRKSVGYi_ktt_2TjxdC56KysWJ_pnEtpIIrhQtxhGwXFJY5OLlaUN6WinyxGxy1bwxVK3G2S6KhvQHlQVvm6W5dSkKWt6mJe1VFmB3ap_4p_v6kcWhgxj7D-ZMVygDHEWTpix4pNoUjgUefP8QKu-YHr4znZ8jdWndR17ymPrlj6ifT923HeoCPQemss-mZ90lLxhFMoPk8') no-repeat fixed;
  background-size: cover;
  color: #333;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}

h1 {
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