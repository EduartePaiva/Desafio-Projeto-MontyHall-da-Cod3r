<template>
 
  <div role="main" class='tela-inicial p-8 bg-gradient-to-r from-green-500 to-blue-500'>
    
    <input type="text">



      <Porta :numPorta="1" ></Porta>
    

  </div>

</template>

<script setup lang="ts">
  import Porta from './components/Porta.vue'



</script>

<style lang="scss" scoped>
  .tela-inicial{
    height: 100vh;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    gap: 32px;
    flex-wrap: wrap;
    overflow:auto;

  }


</style>