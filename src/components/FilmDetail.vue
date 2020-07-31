<template>
  <div>
      <h2>{{ film.title }}</h2>
      <h3>Director</h3>
      <div>{{ film.director }}</div>
      <h3>Release Year</h3>
      <div>{{ film.release_date }}</div>
      <h3>Description</h3>
      <div>{{ film.description }}</div>
  </div>
</template>

<script>
export default {
    name: 'film-detail',
    props: ['film']
}
</script>

<style>

</style>