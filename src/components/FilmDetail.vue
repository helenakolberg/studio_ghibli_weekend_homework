<template>
  <div>
      <h3>{{ film.title }}</h3>
      <h2>Director</h2>
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