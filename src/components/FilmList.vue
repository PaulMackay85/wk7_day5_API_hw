<template lang="html">
  <select @change="handleChange" v-model="selectedFilm">
    <option v-for="film in films" :value="film">{{film.title}}</option>
  </select>
</template>

<script>
import {eventBus} from "../main.js"

export default {
  name: "film-list-select",
  props: ["films"],
  data() {
    return {
      selectedFilm: {}
    }
  },
  methods: {
    handleChange: function(){
      eventBus.$emit("film-selected", this.selectedFilm)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
