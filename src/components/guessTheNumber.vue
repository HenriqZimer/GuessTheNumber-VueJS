<template>
    <div class="guess" >
			<h1>{{ computerNumber }}</h1>
        <h2>Acerte o Numero</h2>
        <h2>1 - 100</h2>
      <h1 v-if="controlador == 1">Voce Ganhou</h1>
      <h1 v-else-if="controlador == 2">Voce Perdeu</h1>
        <btnNovoJogo v-if="controlador == 1 || controlador == 2" @newGameAcionado="newGame" />
        <entradaTexto v-else @inputAcionado="comparativoJogadas"/>
    </div>
</template>

<script>
import entradaTexto from "./entradaTexto.vue"
import btnNovoJogo from './btnNovoJogo.vue';
export default {
  components:{ 
    entradaTexto, 
    btnNovoJogo 
  },
	data(){
		return{
      computerNumber: null,
      controlador: 0,
    }
  },
	methods:{
		newGame(){
    window.location.reload()
		},
    comparativoJogadas(tentativas, numerosJogados, numeroJogado, ultimaJogada) {
      if(ultimaJogada == this.computerNumber){
        this.controlador = 1;
      } else if (tentativas >= 3)
        this.controlador = 2;
    }
  },
	created(){
		this.computerNumber = Math.floor(Math.random() * 100 + 1)
    }
	}
</script>

<style>
  .guess{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    flex-direction: column;
  }
  .h2{
    text-align: center;
  }
</style>