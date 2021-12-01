<template>
  <main>
    
    <div class="card">
      <h3 class="title">TITOLO</h3>
      <p class="original-title">Titolo originale: TITOLO ORIGINALE</p>
      <p class="lang">Lingua: LINGUA</p>
      <p class="rate">Voto: VOTO</p>
    </div>

  </main>
</template>

<script>
export default {
  name: 'Main'
}
</script>

<style lang="scss" scoped>

main{
  height: calc(100vh - 80px);
  background-color: rgb(44, 44, 44);
  padding: 50px;

  .card{
    width: 250px;
    height: 400px;
    background-color: grey;
    color: white;
    padding: 20px;
    
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