<template lang="html">
  <li v-on:click="displayData">{{country.name}}</li>
</template>

<script>
import {eventBus} from '../main.js';
export default {
  name: 'list-component',
  props: ['country'],
  methods: {
    displayData(){
      eventBus.$emit('selected-country',this.country)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
