<template lang="html">
<div v-if='country'>
  <h3>{{country.name}}</h3>
  <p>Capital City: {{country.capital}}</p>
  <p>Population: {{country.population}}</p>
  <h4>Languages:</h4>
  <p v-for='langauge in country.languages'>{{langauge.name}}</p>
  <img :src="country.flag">
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
