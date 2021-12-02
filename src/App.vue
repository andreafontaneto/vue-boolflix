<template>

  <div>
    <Header @startSearch="getFilms" />
    <Main :filmsProps="films"/>
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
      callAPI: 'https://api.themoviedb.org/3/search/movie',
      apiParams: {
        apiKey: 'ad0975316f208f153593af06f9245a6b',
        language: 'it-IT',
        query: ''
      },
      films: []
    }
  },

  methods: {

    getAPI(){
      axios.get(this.callAPI, {params: this.apiParams})
      .then( r => {
        console.log(r.data.results);
        this.films = r.data.results;

        
      })
      .catch( e => {
        console.log(e);
      })
    },

    getFilms(text){
      console.log(text);
      this.apiParams.query = text;
      this.getAPI();
    }

  }

}
</script>

<style lang="scss">

@import "./assets/style/vars.scss";
@import "./assets/style/generals.scss";

</style>
