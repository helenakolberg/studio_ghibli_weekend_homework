<template>
  <div>
      <ul>
          <film-detail v-for="(film, index) in films" :film="film" :key="index"/>
      </ul>
  </div>
</template>

<script>
import FilmDetail from './FilmDetail'

export default {
    name: 'film-list',
    props: ['films'],
    components: {
        "film-detail": FilmDetail
    }
}
</script>

<style>

</style>