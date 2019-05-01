<template lang="html">
  <option :value='country'>{{country.name}}</option>
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
