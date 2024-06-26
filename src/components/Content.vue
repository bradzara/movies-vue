<script>
import axios from "axios";
import MoviesIndex from "./MoviesIndex.vue";

export default {
  components: {
    MoviesIndex,
  },

  data: function() {
    return {
      movies: [
        { id: 1, name: "Alien", image_url: "https://postergirlnyc.myshopify.com/cdn/shop/products/182717571546-0_1200x1200.jpg?v=1563557298", release_year: 1979, run_time: 125  },
        { id: 2, name: "Tropic Thunder", image_url: "https://m.media-amazon.com/images/I/51AQVt+AIVL._AC_UF894,1000_QL80_.jpg", release_year: 2008, run_time: 107 },
        { id: 3, name: "Team America: World Police", image_url: "https://m.media-amazon.com/images/I/51Jf9kKecWL._AC_UF894,1000_QL80_.jpg", release_year: 2004, run_time: 98 },
        { id: 4, name: "Borat", image_url: "https://i.ebayimg.com/images/g/FGUAAOSwNPti~flg/s-l1200.webp", release_year: 2006, run_time: 84 } 
      ],
    };
  },

  created: function () {
    this.handleIndexMovies();
  },
  methods: {
    handleIndexMovies: function () {
      axios.get("http://localhost:3000/movies.json").then((response) => {
        console.log("movies index", response);
        this.movie = response.data;
      });
    },
  },
};

</script>

<template>
  <div id="app">
    <h1>Random Movie Generator</h1>
    <button @click="generateRandomMovie">Generate Random Movie</button>
    <p v-if="randomMovie">{{ randomMovie }}</p>
    <MoviesIndex v-bind:movies="movies"/>
  </div>
</template>

<style>
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
.image-container {
  display: flex;
  justify-content: center;
}
.resized-image {
  width: 400px;
  height: auto;
  margin: 10px;
}
</style>