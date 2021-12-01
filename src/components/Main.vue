<template>
  <main>
    
    <div v-for="film in films" :key="film.id" class="card">
      <h3 class="title">{{film.title}}</h3>
      <p class="original-title">
        Titolo originale:<br>
        {{film.original_title}}
      </p>
      <p class="lang">Lingua: {{film.original_language}}</p>
      <p class="rate">Voto: {{film.vote_average}}</p>
    </div>

  </main>
</template>

<script>

import axios from 'axios';

export default {
  name: 'Main',

  data(){
    return{
      callAPI: 'https://api.themoviedb.org/3/search/movie',
      apiKey: 'ad0975316f208f153593af06f9245a6b',
      query: 'ritorno al futuro',
      films: []
    }
  },

  methods: {

    getApi(){
      axios.get(this.callAPI+'?api_key='+this.apiKey+'&query='+this.query)
      .then( r => {
        console.log(r.data.results);
        this.films = r.data.results;
      })
      .catch( e => {
        console.log(e);
      })
    }

  },

  mounted(){
    this.getApi();
  }
}
</script>

<style lang="scss" scoped>

main{
  // height: calc(100vh - 80px);
  background-color: rgb(44, 44, 44);
  padding: 50px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;

  .card{
    width: 250px;
    height: 400px;
    background-color: grey;
    color: white;
    padding: 20px;
    margin: 0 20px 50px 20px;
    
    .title{
      text-align: center;
      padding-bottom: 20px;
    }

    .original-title,
    .lang,
    .rate{
      font-size: 12px;
      padding-bottom: 20px;
    }
  }
}

</style>