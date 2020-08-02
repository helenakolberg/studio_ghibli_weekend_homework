<template>
  <div class="detail-film">
      <h2>{{ film.title }}</h2>
      <h3>Director</h3>
      <div>{{ film.director }}</div>
      <h3>Release Year</h3>
      <div>{{ film.release_date }}</div>
      <h3>Description</h3>
      <div>{{ film.description }}</div>
      <button class="add-button" @click="handleClick(film)">Add To My To-Watch List</button>
  </div>
</template>

<script>
import {eventBus} from '@/main.js'

export default {
    name: 'film-detail',
    props: ['film'],
    methods: {
      handleClick(film) {
        eventBus.$emit('to-watch', this.film)
      }
    }
}
</script>

<style>

.add-button {
  margin-top: 20px;
}

.detail-film {
  border: solid white 3px;
  border-radius: 14px;
  width: 400px;
  height: auto;
  padding: 10px;
  margin: auto;
}

</style>