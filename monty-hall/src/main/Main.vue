<template>
    <div role="main" class='tela-inicial p-8 bg-gradient-to-r from-green-500 to-blue-500'>
        <Overlay v-if="mensagemDeErro" @click="clickMensagemDeErro" :mensagemOverlay="mensagemDeErro"></Overlay>

        <form 
            :onSubmit="form" 
            v-if="novoItem === 0" 
            :class="`
                formulario flex flex-col p-4 bg-white bg-opacity-20
                rounded-2xl shadow-lg shadow-slate-700 font-mono text-lg
            `">

            <label for="numPortas">Número de Portas</label><br>
            <input class="shadow-sm shadow-black" type="number" id="numPortas" placeholder="Numéro de Portas"><br>
            <label for="qualPorta">Qual Porta?</label><br>
            <input class="shadow-sm shadow-black"  type="number" id="qualPorta" placeholder="Escolha a verdadeira"><br>
            <input class="butao shadow-sm shadow-black hover:cursor-pointer"  type="submit" value="Enviar">
        </form>

        <div v-for="portas in novoItem" :key="portas">
            <Porta :numPorta="portas" :portaPremiada="portas === portaPremiada" @diminuirNumPortas="diminuirPortas"></Porta>
        </div>
    </div>
</template>

<script lang="ts">
import Overlay from '../components/Overlay.vue'
import Porta from '../components/Porta.vue'
import { defineComponent } from 'vue'



export default defineComponent({
    components: { Porta, Overlay },

    data() {
        return {
            mensagemDeErro: '',
            novoItem: 0,
            portaPremiada: 0,
            portasAbertas: 0
        }
    },
    methods: {
        form(e: any) {
            e.preventDefault()
            const numPortas = e.target.numPortas.value
            const qualPorta = e.target.qualPorta.value

            if (numPortas === '' || qualPorta === '') {
                this.mensagemDeErro = 'Erro: Formulário não preenchido'
                return
            }
            if (numPortas > 30) {
                this.mensagemDeErro = 'Erro: Número máximo de portas é 30'
                return
            }
            const verdade = (numPortas - qualPorta) > -1 && numPortas > 0 && qualPorta > 0
            if (!verdade) {
                this.mensagemDeErro = 'Erro: Valor incorreto'
                return
            }
            const numPortasInt = Number.parseInt(numPortas)
            this.novoItem = numPortasInt
            this.portasAbertas = numPortasInt
            this.portaPremiada = Number.parseInt(qualPorta)
        },

        diminuirPortas(){
            this.portasAbertas--

            if(this.portasAbertas == 0){
                this.mensagemDeErro = 'Todas as Portas abertas. Reiniciando o Jogo'
                
            }
        },

        clickMensagemDeErro(){
            if(this.mensagemDeErro === 'Todas as Portas abertas. Reiniciando o Jogo'){
                this.novoItem= 0
                this.portaPremiada= 0
                this.portasAbertas= 0
            }
            this.mensagemDeErro = ''
        }
    }

})


</script>

<style lang="scss" scoped>
    .tela-inicial {
        height: 100vh;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        gap: 32px;
        flex-wrap: wrap;
        overflow: auto;
    }

    .formulario{

        align-items: center;

        input{
            background-color: white;
            margin-bottom: 10px;
            padding: 5px;
            border-radius: 5px;
        }
        input:focus{
            outline: none;
            background-color: rgba(56, 92, 56, 0.201);
            color: white;
        }
        input:focus::placeholder{
            color: transparent;
        }
        .butao{
            margin-bottom: 0px;
            
        }
        .butao:hover{
            background-color: rgba(56, 92, 56, 0.201);
            color: white;
        }
    }



</style>