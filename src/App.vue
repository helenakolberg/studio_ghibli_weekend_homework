<template>
  <div>
    <film-select />
  </div>
</template>

<script>
import FilmSelect from './components/FilmSelect';

export default {
  data() {
    return {
      films: []
    }
  },
  mounted() {
    fetch("https://ghibliapi.herokuapp.com/films")
      .then(response => response.json())
      .then(data => this.films = data)

  },
  components: {
    "film-select": FilmSelect
  }
}
</script>

<style>

</style>