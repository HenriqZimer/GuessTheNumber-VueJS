<template>
    <div class="guess" >
			<h1>{{ computerNumber }}</h1>
        <h2>Acerte o Numero</h2>
        <h2>1 - 100</h2>
        <entradaTexto @inputAcionado="verificadorResposta"/>
        <div>
          <h1 v-if="controlador == 1">Voce Ganhou</h1>
        </div>
        <btnNovoJogo @newGameAcionado="newGame" />
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
      computerNumber: 10,
      controlador: 0,
    }
  },
	methods:{
		newGame(){
    window.location.reload()
		},
    handleChange(event) {
      console.log(event.target.value); 
    },
    comparativoResultado(tentativas){
      if(tentativas >= 2){
        this.controlador = 1
    }
  },
  verificadorResposta(numerosJogados){
    console.log(numerosJogados + 'henriu')

    if(numerosJogados == this.computerNumber){
      this.controlador = 1
    }
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