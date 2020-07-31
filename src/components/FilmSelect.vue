<template>
  <div>
      <select @change="handleChange" v-model="selectChangeFilm">
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

</style>