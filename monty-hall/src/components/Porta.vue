<template>
    <div @click="AbrirPorta" 
        :class="portaAberta ? 'porta border-solid border-4 border-red-900 bg-black bg-opacity-50' : 'porta bg-amber-600 border-solid border-4 border-yellow-300'">


        <div v-if="!portaAberta" class=" numero text-yellow-300 select-none text-center mt-3 text-2xl font-bold">
             {{ numPorta }}
        </div>
        <div v-if="!portaAberta" class="macaneta bg-yellow-300 rounded-full ml-2"></div>

        <div v-if="portaAberta && portaPremiada" >Presente</div>
        <div class="base bg-gray-300">
        </div>

    </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue'

export default defineComponent({

    props: {
        numPorta: Number,
        portaPremiada: Boolean,
    },
    
    data(){
        return {
            portaAberta: true,
        }
    },
    methods: {
        AbrirPorta(){
            this.portaAberta = !this.portaAberta
            console.log(this.portaPremiada)
            this.$emit('diminuirNumPortas')
        }
    }
})
</script>

<style lang="scss" scoped>

.portaEstaFechada{
    height: 180px;
    width: 100px;
    min-width: 100px;
    position: relative;
    box-sizing: border-box;

    border-bottom: none;
}

.porta{
    height: 180px;
    width: 100px;
    min-width: 100px;
    position: relative;
    box-sizing: border-box;

    border-bottom: none;
    .macaneta{
        width: 12px;
        height: 12px;
        top: 50%;
        transform: translate(0,-50%);
        position: absolute;
    }

    .base{
        height: 4px;
        width: 106px;
        position: absolute;
        z-index: 100;
        top: 173px;
        left: -7px;
    }
}



</style>