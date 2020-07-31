<template>
  <div>
      <ul>
          <li v-for="film in films">{{ film.title }}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'film-list',
    props: ['films']
}
</script>

<style>

</style>