<template>
  <div>
      <ul>
        <li id="empty-to-watch" v-if="toWatch.length === 0">
            Oh no! There is nothing on your to-watch list!
            <button @click="handleLuckyDip">Lucky Dip</button>
        </li>
        <li v-for="(film, index) in toWatch" :key="index">
            {{ film.title }}, {{ film.release_date }}
            <button @click="handleClick(film)">Watched!</button>
        </li>
      </ul>
  </div>
</template>

<script>
import {eventBus} from '@/main.js'

export default {
    name: 'to-watch',
    props: ['favourites'],
    data() {
        return {
            toWatch: []
        }
    },
    mounted() {
        eventBus.$on('to-watch', (film) => {
            if (this.toWatch.includes(film) === false) this.toWatch.push(film);
        })
    },
    methods: {
        handleClick(film) {
            const index = this.toWatch.indexOf(film);
            this.toWatch.splice(index, 1);
        },

        handleLuckyDip() {
            const film = this.favourites[Math.floor(Math.random() * this.favourites.length)];
            this.toWatch.push(film);
        }
    }
}
</script>

<style>

#empty-to-watch {
    font-size: 14px;
}

</style>