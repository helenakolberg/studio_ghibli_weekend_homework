<template>
  <div>
      <ul>
          <list-item v-for="(film, index) in films" :film="film" :key="index"/>
      </ul>
  </div>
</template>

<script>
import ListItem from './ListItem'

export default {
    name: 'film-list',
    props: ['films'],
    components: {
        "list-item": ListItem
    }
}
</script>

<style>

</style>