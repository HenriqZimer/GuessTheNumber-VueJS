<template>
  <div class="guess">
      <h1>Acerte o Numero entre 1 - 100</h1>
      <h6>Você tem 10 chances para acertar</h6>
    <div>
      <h1 v-if="controlador == 1">Voce Ganhou</h1>
      <h1 v-else-if="controlador == 2">Voce Perdeu</h1>
    </div>
      <btnNovoJogo @newGameAcionado="newGame" v-if="controlador == 1 || controlador == 2" />
        <entradaTexto v-else
          @inputAcionado="comparativoJogadas"
          :numeroRandom="numeroRandom" />
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
      numeroRandom: null,
      controlador: 0,
    }
  },
	methods:{
		newGame(){
    window.location.reload()
		},
    comparativoJogadas(tentativas, numerosJogados, numeroJogado, ultimaJogada) {
      if(ultimaJogada == this.numeroRandom){
        this.controlador = 1;
      } else if (tentativas >= 10)
        this.controlador = 2;
    }

  },
	created(){
		this.numeroRandom = Math.floor(Math.random() * 100 + 1)
    console.log(this.numeroRandom)
    }
	}
</script>

<style scoped>
  .guess {
  font-family: Arial, sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

.guess h2 {
  font-size: 24px;
  color: #333;
  margin-bottom: 10px;
}

.guess h6 {
  font-size: 18px;
  color: #666;
  margin-bottom: 20px;
}

.guess h1 {
  font-size: 36px;
  margin-top: 30px;
  color: rgb(0, 0, 0);
  
}

</style>