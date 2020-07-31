<template>
  <div>
      <h2>{{ film.title }}</h2>
      <h3>Director</h3>
      <div>{{ film.director }}</div>
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