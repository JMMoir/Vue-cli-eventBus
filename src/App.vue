<template lang="html">
  <div class="">
  <h1>Countries</h1>
  <input type="text" v-model='searchValue' placeholder="search countries">
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
      selectedCountry: null,
      searchValue: ''
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
  },
  computed:{
    searchCountries(){
      return this.countries.filter((country) => {
        return country.name.match(this.searchValue)
      })
    }
  }
}
</script>

<style lang="css" scoped>
</style>
