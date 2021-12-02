<template>

  <div>
    <Header @startSearch="getFilms(); getSeries();" />
    <Main :filmsProps="films" :seriesProps="series"/>
  </div>
  
</template>

<script>

import axios from 'axios';

import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: 'App',
  components: {
    Header,
    Main
  },

  data(){
    return{
      callAPI: 'https://api.themoviedb.org/3/search/',
      typeMovies: 'movie', 
      typeSeries: 'tv', 
      apiParams: {
        api_key: 'ad0975316f208f153593af06f9245a6b',
        language: 'it-IT',
        query: ''
      },
      films: [],
      series: []
    }
  },

  methods: {

    getAPI(){
      axios.get(this.callAPI+this.typeMovies, {params: this.apiParams})
      .then( r => {
        console.log(r.data.results);
        this.films = r.data.results;
      })
      .catch( e => {
        console.log(e);
      })
    },

    getAPIseries(){
      axios.get(this.callAPI+this.typeSeries, {params: this.apiParams})
      .then( r => {
        console.log(r.data.results);
        this.series = r.data.results;
      })
      .catch( e => {
        console.log(e);
      })
    },

    getFilms(text){
      console.log(text);
      this.apiParams.query = text;
      this.getAPI();
    },

    getSeries(text){
      console.log(text);
      this.apiParams.query = text;
      this.getAPIseries();
    }

  }

}
</script>

<style lang="scss">

@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";

</style>
