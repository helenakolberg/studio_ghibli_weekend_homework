<template>
  <div>
      <select class="select" @change="handleChange" v-model="selectChangeFilm">
          <option value=null disabled selected>Choose a Film</option>
          <option v-for="(film, index) in dropDownFilms" :key="index" v-bind:value="film">{{ film.title }}</option>
      </select>
  </div>
</template>

<script>
import {eventBus} from '@/main.js'

export default {
    name: 'film-select',
    data() {
        return {
            selectChangeFilm: null
        }
    },
    props: ['dropDownFilms'],
    methods: {
        handleChange() {
            eventBus.$emit('selected-film', this.selectChangeFilm)
        }
    }

}
</script>

<style>

.select {
    background: transparent;
    border: solid white 2px;
    padding: 10px;
    color: white;
}

.select:hover {
    background: transparent;
    border: solid white 2px;
    padding: 10px;
    color: white;
    font-style: italic;
    cursor: pointer;
}

.select:focus, .select:visited{
    background: transparent;
    border: solid white 2px;
    padding: 10px;
    color: white;
    outline: none;

}
</style>