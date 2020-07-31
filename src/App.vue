<template>
  <div>
    <film-select :dropDownFilms="films" />
  </div>
</template>

<script>
import FilmSelect from './components/FilmSelect';
import FilmDetail from './components/FilmDetail'

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
    "film-select": FilmSelect,
    "film-detail": FilmDetail
  }
}
</script>

<style>

</style>