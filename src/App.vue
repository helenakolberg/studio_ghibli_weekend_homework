<template>
  <div>
    <h1>Studio Ghibli Films</h1>
    <div id="chart-label">Studio Ghibli films are directed by:</div>
    <pie-chart id="chart" :pieChartFilms="films"/>
    <div id="options">
      <div>
        <button @click="handleClick">View All Films</button>
      </div>
      <div id="pipe">|</div>
      <div>
        <film-select :dropDownFilms="films" />
      </div>
    </div>  
    <film-detail v-if="!isClicked && selectedFilm" :film="selectedFilm" />
    <film-list v-if="isClicked" :films="films" />
    <h2 id="watch-title">To Watch</h2>
    <to-watch :favourites="films" />
  </div>
</template>

<script>
import {eventBus} from '@/main.js'
import FilmSelect from './components/FilmSelect';
import FilmDetail from './components/FilmDetail'
import FilmList from './components/FilmList';
import PieChart from './components/PieChart'
import ToWatch from './components/ToWatch'

export default {
  data() {
    return {
      films: [],
      selectedFilm: null,
      isClicked: false
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
    "pie-chart": PieChart,
    "to-watch": ToWatch
  }
}
</script>

<style>

body {
  background-color: #393939;
  background-image: url("../public/totoro.png");
  background-repeat: no-repeat;
  background-position: right top;
  background-size: 500px 300px;
  height: 700px;
  color: #ffffff;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

#options {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 30px;
}

#options>div {
  margin: 20px;
}

#pipe {
  font-size: 28px;
}

button {
  background: transparent;
  border: solid white 2px;
  padding: 10px;
  color: white;
}

button:hover {
  background: transparent;
  border: solid white 2px;
  padding: 10px;
  color: white;
  font-style: italic;
  cursor: pointer;
}

button:focus {
  background: transparent;
  border: solid white 2px;
  padding: 10px;
  color: white;
  font-style: italic;
  cursor: pointer;
  outline: none;
}

ul {
  padding-left: 0px;
}

li {
  list-style-type: none;
  margin-left: 50px;
  margin-bottom: 8px;
}

h1 {
  margin: 50px;
}

#chart-label {
  margin-left: 300px;
  margin-top: 80px;
  font-size: 14px;
}

#watch-title {
  margin: 50px;
}

</style>