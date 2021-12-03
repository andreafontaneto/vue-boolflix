<template>
  <main>

    <h2 v-if="filmsProps.length > 0" class="category">FILMS TROVATI</h2>

    <div class="films-box">

      <div v-for="film in filmsProps" :key="film.id" class="card">

        <div class="cover-box">
          <img v-if="film.poster_path" 
          :src="`https://image.tmdb.org/t/p/w342/${film.poster_path}`" :alt="film.original_title">
          <img v-else :src="`https://www.npcmagazine.it/wp-content/themes/fox/images/placeholder.jpg`"
          :alt="film.original_title">
        </div>

        <div class="card-info">
          <div class="title-box">
            <h3 class="title">{{film.title}}</h3>
            <p v-if="film.original_title !== film.title" class="original-title">
              Titolo originale:{{film.original_title}}
            </p>
          </div>

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

          <div v-if="film.overview" class="story">
            <p>Trama:</p>
            <p>{{film.overview}}</p>
          </div>
          <div v-else class="no-story">
            <p>Trama: Ci spiace! Forse la storia non è così avvincente da essere caricata...</p>
          </div>
        </div>

      </div>

    </div>

    <h2 v-if="seriesProps.length > 0" class="category">SERIE TV TROVATE</h2>

    <div class="series-box">

      <div v-for="serie in seriesProps" :key="serie.id" class="card">

        <div class="cover-box">
          <img v-if="serie.poster_path" 
          :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`" :alt="serie.original_name">
          <img v-else :src="`https://www.npcmagazine.it/wp-content/themes/fox/images/placeholder.jpg`"
          :alt="serie.original_name">
        </div>

        <div class="card-info">
          <div class="title-box">
            <h3 class="title">{{serie.name}}</h3>
            <p v-if="serie.original_name !== serie.name" class="original-title">
              Titolo originale:{{serie.original_name}}
            </p>
          </div>

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

          <div v-if="serie.overview" class="story">
            <p>Trama:</p>
            <p>{{serie.overview}}</p>
          </div>
          <div v-else class="no-story">
            <p>Trama: Ci spiace! Forse la storia non è così avvincente da essere caricata...</p>
          </div>
        </div>

      </div>

    </div>


    <div v-if="errorMsg" class="error-message">
      <p>ERRORE! NON E' STATO TROVATO NIENTE CON QUEL NOME</p>
    </div>

  </main>
</template>

<script>

export default {
  name: 'Main',

  props: {
    filmsProps: Array,
    seriesProps: Array,
    errorMsg: Boolean
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
  min-height: calc(100vh - 80px);
  background-color: rgb(44, 44, 44);
  padding: 50px;

  .category{
    color: white;
    margin-bottom: 30px;
  }

  .films-box,
  .series-box{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  .card{
    width: 300px;
    color: white;
    padding: 20px;
    margin: 0 20px 50px 20px;
    position: relative;

    transition: padding 0.5s;

    .cover-box{
      background-color: rgba(0, 0, 0, 0.0);

      transition: all 0.5s;

      // img{
      //   height: 392px;
      // }
    }

    .card-info{
      // display: none;
      height: 450px;
      padding: 20px;
      position: absolute;
      top: 0;
      left: 0;
      visibility: hidden;
      opacity: 0;

      transition: visibility 0.5s, opacity 0.5s;

      .title-box{
        height: 110px;
      }
      
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
        padding-bottom: 20px;
  
        .flag{
          width: 50px;
        }
      }
  
      .story,
      .no-story{
        height: 210px;
        overflow: scroll;
      }
  
      .no-story{
        font-style: italic;
        color: grey;
      }

    }
      
  }

  .card:hover{
    padding: 0;

    .cover-box{
      background-color: rgba(0, 0, 0, 0.8);
    
    }

    .card-info{
      background-color: rgba(0, 0, 0, 0.8);
      visibility: visible;
      opacity: 1;
    }
  }

  .error-message{
    font-size: 30px;
    font-style: italic;
    color: tomato;
  }



}

</style>