<template>
  <div>
    <li @click="handleClick">
        <div>{{ film.title }}, {{ film.release_date }}</div>
        <div>Directed by {{ film.director }}</div>
    </li>
  </div>
</template>

<script>
import {eventBus} from '@/main.js'

export default {
    name: 'list-item',
    props: ['film'],
    methods: {
        handleClick() {
            eventBus.$emit('film-from-list', this.film)
        }
    }
}
</script>

<style>

</style>