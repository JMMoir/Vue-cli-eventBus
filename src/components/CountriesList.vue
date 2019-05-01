<template lang="html">
  <div>
      <h1>List</h1>
      <select v-on:change="displayData" v-model="selectedCountry">
        <list-component v-for="(country, index) in countries" :country="country" :key="index"></list-component>
      </select>
  </div>

</template>

<script>
import ListComponent from './ListComponent.vue'
import {eventBus} from '../main.js'

export default {
  name: "countries-list",
  data(){
    return{
      selectedCountry: null
    }
  },

  props:['countries', 'country'],

  components:{
    "list-component": ListComponent
  },
  methods: {
    displayData(){
      eventBus.$emit('selected-country',this.selectedCountry)
    },

  }
}
</script>

<style lang="css" scoped>
</style>
