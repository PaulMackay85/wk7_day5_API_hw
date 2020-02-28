<template>
  <div id="app">
    <h1>Studio Ghibli API</h1>
    <div class="container">
      <film-list-select :films="films" />
      <film-details :film="selectedFilm" />
    </div>
  </div>
</template>

<script>
import FilmList from "./components/FilmList.vue";
import FilmDetails from "./components/FilmDetails.vue";
import {eventBus} from "./main.js";

export default {
  data() {
    return {
      films: [],
      selectedFilm: {}
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then(data => this.films = data)

    eventBus.$on("film-selected", (film) => {
      this.selectedFilm = film;
    })
  },
  components: {
    "film-list-select": FilmList,
    "film-details": FilmDetails
  }
}
</script>

<style>

h1 {
  font-family: fantasy;
  color: #C8A2C8;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  display: inline-block;
  width: 60%;
}
</style>
