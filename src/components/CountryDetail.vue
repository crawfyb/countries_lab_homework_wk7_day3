<template lang="html">
  <div v-if='country'>
<h3>Name: {{country.name}}</h3>
<p>Capital: {{country.capital}}</p>
<p>population: {{country.population}}</p>
  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
</style>
