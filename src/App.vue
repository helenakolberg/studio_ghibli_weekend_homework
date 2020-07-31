<template>
  
</template>

<script>
export default {
  data() {
    return {
      films: []
    }
  },
  mounted() {
    fetch("https://ghibliapi.herokuapp.com/films")
      .then(response => response.json())
      .then(data => this.films = data)

  }
}
</script>

<style>

</style>