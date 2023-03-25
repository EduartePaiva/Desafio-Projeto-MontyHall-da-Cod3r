<template>
    <div role="main" class='tela-inicial p-8 bg-gradient-to-r from-green-500 to-blue-500'>
    

    
    <input v-model="novoItem" type="number" placeholder="Numéro de Portas">

    <div v-for="portas in novoItem" :key="portas">
        
        <Porta :numPorta="portas" ></Porta>
        
    
    </div>

    

  </div>
</template>

<script lang="ts">
    import Porta from '../components/Porta.vue'
    import { defineComponent } from 'vue'

    export default defineComponent ({
        components: { Porta },
        props: {
            novoItem: Number

        },

        data(){
            return {
                novoItem: 0
            }
        }

    })


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