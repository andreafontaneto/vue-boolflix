<template>
  <header>
    
    <h1>BOOLFLIX</h1>

    <div class="search-box">
      <input type="text" placeholder="Cerca il film o serie tv...">
      <button>CERCA</button>
    </div>


  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang="scss" scoped>

header{
  width: 100vw;
  height: 80px;
  background-color: black;
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  h1{
    color: red;
  }

  input{
    width: 300px;
    height: 30px;
    margin-right: 20px;
  }

  button{
    width: 100px;
    height: 30px;
    background-color: deepskyblue;
    color: white;
  }
}

</style>