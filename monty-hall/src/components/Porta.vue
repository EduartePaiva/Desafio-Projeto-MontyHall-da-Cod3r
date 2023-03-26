<template>
    <div @click="AbrirPorta" 
        :class="portaAberta ? 'porta border-solid border-4 border-red-900 bg-black bg-opacity-50' : 'porta bg-amber-600 border-solid border-4 border-yellow-300'">


        <div v-if="!portaAberta" class=" numero text-yellow-300 select-none text-center mt-3 text-2xl font-bold">
             {{ numPorta }}
        </div>
        <div v-if="!portaAberta" class="macaneta bg-yellow-300 rounded-full ml-2"></div>
        <Presente v-if="portaAberta && portaPremiada"/>
        <div class="base bg-gray-300">
        </div>

    </div>
</template>

<script lang="ts">
import Presente from '../components/Presente.vue'
import { defineComponent } from 'vue'

export default defineComponent({
    components: {Presente},
    props: {
        numPorta: Number,
        portaPremiada: Boolean,
    },
    
    data(){
        return {
            portaAberta: false,
        }
    },
    methods: {
        AbrirPorta(){
            if(!this.portaAberta){
                this.portaAberta = true
                console.log(this.portaPremiada)
                this.$emit('diminuirNumPortas')
            }
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
        top: 173px;
        left: -7px;
    }
}

</style>