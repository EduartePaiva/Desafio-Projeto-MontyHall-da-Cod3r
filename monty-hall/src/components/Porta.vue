<template>
    <div @click="selecionarPorta" 
    
        :class="`
            porta border-solid border-4
            ${estadoDaPorta === 'aberta' ? ' bg-black bg-opacity-50':'bg-amber-600 '}
            ${portaSelecionada && estadoDaPorta !== 'aberta' ? 'border-yellow-300' : 'border-red-900'} 
        `">

        <div v-if="estadoDaPorta !== 'aberta' "
            :class="`
                numero  select-none text-center mt-3 text-2xl font-bold
                ${portaSelecionada ? 'text-yellow-300': 'text-white'}
            `">
             {{ numPorta }}
        </div>
        <div v-if="estadoDaPorta !== 'aberta'"  @click="AbrirPorta" 
            :class="`
                macaneta  rounded-full ml-2
                ${portaSelecionada ? 'bg-yellow-300' : 'bg-red-900'}
            `"
        />
        

        <Presente v-if="estadoDaPorta === 'aberta' && portaPremiada"/>
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
            estadoDaPorta: 'padrao',
            portaSelecionada: false
        }
    },
    methods: {
        AbrirPorta(){
            if(this.estadoDaPorta !== 'aberta'){
                this.estadoDaPorta = 'aberta'
                this.$emit('diminuirNumPortas')
            }
        },

        selecionarPorta(){
            if(this.estadoDaPorta !== 'aberta') this.portaSelecionada = !this.portaSelecionada
        }
    }
})
</script>

<style lang="scss" scoped>

.d-none{
    display: none;
}
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