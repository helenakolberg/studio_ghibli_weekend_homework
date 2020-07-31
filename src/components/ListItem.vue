<template>
  <div>
      <li>{{ film.title }}, {{ film.release_date }}</li>
  </div>
</template>

<script>
export default {
    name: 'list-item',
    props: ['film']
}
</script>

<style>

</style>