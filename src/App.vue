<template>
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <select id="country_select" v-model="selectedCountry">
  			<option disabled value="">Select a country</option>
  			<option v-for="country in countries" :value="country">{{country.name}}</option>
  		</select>

      <img v-if="selectedCountry" :src="selectedCountry.flag" alt="country flag">


      <country-detail :country='selectedCountry'></country-detail>

    </div>
  </div>

</template>

<script>
import { eventBus }from './main.js';
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';

export default {
  name: 'app',
  data() {
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted() {
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries);

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
components: {
  "countries-list": CountriesList,
  "country-detail": CountryDetail
  }
}
</script>

<style>
.main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
