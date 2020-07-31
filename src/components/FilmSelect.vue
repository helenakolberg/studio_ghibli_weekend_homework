<template>
  <div>
      <select>
          <option v-for="(film, index) in films" :key="index" v-bind:value="film">{{ film.title }}</option>
      </select>
  </div>
</template>

<script>
export default {
    name: 'film-select',
    props: ['films']

}
</script>

<style>

</style>