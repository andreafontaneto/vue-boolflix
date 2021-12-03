<template>
  <main>

    <h2 v-if="filmsProps.length > 0">FILMS</h2>

    <div class="films-box">

      <div v-for="film in filmsProps" :key="film.id" class="card">

        <h3 class="title">{{film.title}}</h3>
        <p v-if="film.original_title !== film.title" class="original-title">
          Titolo originale:<br>
          {{film.original_title}}
        </p>

        <img v-if="film.poster_path" 
        :src="`https://image.tmdb.org/t/p/w342/${film.poster_path}`" :alt="film.original_title">
        <img v-else :src="`https://www.npcmagazine.it/wp-content/themes/fox/images/placeholder.jpg`" :alt="film.original_title">

        <div class="flags">
          <img v-if="film.original_language === 'it'" :src="flags.ita" alt="" class="flag">
          <img v-else-if="film.original_language === 'en'" :src="flags.eng" alt="" class="flag">
          <p v-else class="lang">Lingua: {{film.original_language}}</p>
        </div>

        <i 
        v-for="(star, index) in 5" :key="index" 
        :class=" index < Math.round(film.vote_average/2) ? 'fas' : 'far' " 
        class="fa-star rate">
        </i>

      </div>

    </div>




    <h2 v-if="seriesProps.length > 0">SERIE TV</h2>

    <div class="series-box">

      <div v-for="serie in seriesProps" :key="serie.id" class="card">

        <h3 class="title">{{serie.name}}</h3>
        <p v-if="serie.original_name !== serie.name" class="original-title">
          Titolo originale:<br>
          {{serie.original_name}}
        </p>

        <img v-if="serie.poster_path" 
        :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`" :alt="serie.original_name">
        <img v-else :src="`https://www.npcmagazine.it/wp-content/themes/fox/images/placeholder.jpg`" :alt="serie.original_name">

        <div class="flags">
          <img v-if="serie.original_language === 'it'" :src="flags.ita" alt="" class="flag">
          <img v-else-if="serie.original_language === 'en'" :src="flags.eng" alt="" class="flag">
          <p v-else class="lang">Lingua: {{serie.original_language}}</p>
        </div>
        

        <i 
        v-for="(star, index) in 5" :key="index" 
        :class=" index < Math.round(serie.vote_average/2) ? 'fas' : 'far' " 
        class="fa-star rate">
        </i>

      </div>

    </div>
    

  </main>
</template>

<script>

export default {
  name: 'Main',

  props: {
    filmsProps: Array,
    seriesProps: Array
  },

  data(){
    return{
      flags: {
        ita: require('../assets/img/it.png'),
        eng: require('../assets/img/en.png')
      }
    }
  },

  methods: {

  }
}
</script>

<style lang="scss" scoped>

@import '~@fortawesome/fontawesome-free/css/all.min.css';

main{
  // height: calc(100vh - 80px);
  background-color: rgb(44, 44, 44);
  padding: 50px;

  .films-box,
  .series-box{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
  

  .card{
    width: 250px;
    // height: 400px;
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

    .flags{
      padding-bottom: 10px;
      display: flex;
      justify-content: center;

      .flag{
        width: 50px;
      }
    }

  }
}

</style>