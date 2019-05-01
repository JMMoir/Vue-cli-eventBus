<template lang="html">

  <div>
    
  </div>

</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: "search",
  data(){
    return{
      searchValue: ''
    }
  },
  props:['country', 'countries'],

  methods:{
    searchFunction(){
      eventBus.$emit('selected-country',this.country)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
