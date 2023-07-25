<template>
    <div id="welcomeScreen" >
			<h1>{{ computerNumber }}</h1>
        <h2>Guess the Number <br />1 - 100</h2>
        <h3>Sua Tentativa</h3>
        <entradaTexto />
        <h5>Numero de Tentativas</h5>
        <h5>Suas Tentativas</h5>
        <btnNovoJogo />
    </div>
</template>

<script>
import entradaTexto from "./entradaTexto.vue"
import btnNovoJogo from './btnNovoJogo.vue';
export default {
  components:{ entradaTexto, btnNovoJogo },
		data(){
			return{
			computerNumber: 10,
			}
  },
		methods:{
			newGame(){
    window.location.reload()
		},
	created(){
		this.computerNumber = 10
	}
}
}
</script>

<style>

</style>