<template>
  <div id="details">
    <film-detail class="detail-item" v-for="(film, index) in films" :film="film" :key="index"/></div>
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

#details {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
}

.detail-item {
    width: 300px;
    height: auto;
    margin: 20px;
    border: solid white 3px;
    border-radius: 14px;
    padding: 10px;
}
</style>