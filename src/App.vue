<template>
  <div>
    <h1>Studio Ghibli Films</h1>
    <div>
      <button @click="handleClick">View All Films</button>
    </div>
    <div>
      <film-select :dropDownFilms="films" />
    </div>
    <film-detail v-if="!isClicked && selectedFilm" :film="selectedFilm" />
    <film-list v-if="isClicked" :films="films" />
    <pie-chart :pieChartFilms="films"/>
  </div>
</template>

<script>
import {eventBus} from '@/main.js'
import FilmSelect from './components/FilmSelect';
import FilmDetail from './components/FilmDetail'
import FilmList from './components/FilmList';
import PieChart from './components/PieChart'

export default {
  data() {
    return {
      films: [],
      selectedFilm: null,
      isClicked: false,
      toWatch: []
    }
  },
  methods: {
    handleClick() {
      this.isClicked = true
    }
  },
  mounted() {
    fetch("https://ghibliapi.herokuapp.com/films")
      .then(response => response.json())
      .then(data => this.films = data)

    eventBus.$on('selected-film', (film) => {
      this.selectedFilm = film;
      if (this.isClicked === true) this.isClicked = false;
    })

    eventBus.$on('film-from-list', (film) => {
      this.selectedFilm = film;
      if (this.isClicked === true) this.isClicked = false;
    })

  },
  components: {
    "film-select": FilmSelect,
    "film-detail": FilmDetail,
    "film-list": FilmList,
    "pie-chart": PieChart
  }
}
</script>

<style>

</style>