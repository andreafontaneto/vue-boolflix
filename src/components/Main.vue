<template>
  <main>
    
    <div v-for="film in filmsProps" :key="film.id" class="card">
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

export default {
  name: 'Main',

  props: {
    filmsProps: Array
  },

  data(){
    return{

    }
  },

  methods: {

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