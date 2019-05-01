<template lang="html">
  <div class="">
  <h1>Countries</h1>
  <countries-list :countries='countries'></countries-list>
  <country-detail :country='selectedCountry'></country-detail>
  </div>
</template>

<script>
import countrieslist from './components/CountriesList.vue';
import countrydetail from './components/CountryDetail.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data(){
    return{
      countries: [],
      selectedCountry: null
    };
  },
  components: {
    "countries-list": countrieslist,
    'country-detail': countrydetail
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(response => response.json())
    .then(countries => this.countries = countries);

    eventBus.$on('selected-country', (country) =>{
      this.selectedCountry = country;
    });
  }
}
</script>

<style lang="css" scoped>
</style>
