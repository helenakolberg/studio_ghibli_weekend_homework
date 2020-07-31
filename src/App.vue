<template>
  <div>
    <film-select :dropDownFilms="films" />
    <film-detail v-if="selectedFilm" :film="selectedFilm" />
  </div>
</template>

<script>
import {eventBus} from '@/main.js'
import FilmSelect from './components/FilmSelect';
import FilmDetail from './components/FilmDetail'

export default {
  data() {
    return {
      films: [],
      selectedFilm: null
    }
  },
  mounted() {
    fetch("https://ghibliapi.herokuapp.com/films")
      .then(response => response.json())
      .then(data => this.films = data)

    eventBus.$on('selected-film', (film) => {
      this.selectedFilm = film
    })  

  },
  components: {
    "film-select": FilmSelect,
    "film-detail": FilmDetail
  }
}
</script>

<style>

</style>