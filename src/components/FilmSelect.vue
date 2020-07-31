<template>
  <div>
      <select>
          <option v-for="(film, index) in dropDownFilms" :key="index" v-bind:value="film">{{ film.title }}</option>
      </select>
  </div>
</template>

<script>
export default {
    name: 'film-select',
    props: ['dropDownFilms']

}
</script>

<style>

</style>