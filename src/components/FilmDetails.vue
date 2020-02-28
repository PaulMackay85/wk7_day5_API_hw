<template lang="html">
  <div>
    <h2>{{film.title}}</h2>
    <p>Director: {{film.director}}</p>
    <p>Release Year: {{film.release_date}}</p>
    <p>Rotten Tomatoes Score: {{film.rt_score}}%</p>
    <p>{{film.description}}</p>
  </div>
</template>

<script>
export default {
  name: "film-details",
  props: ["film"]
}
</script>

<style lang="css" scoped>

h2 {
  color: #71EEB8;
}

</style>
