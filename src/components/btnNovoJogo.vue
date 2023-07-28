<template>
	<button class="buttonNewGame" @click="newGameClicado">Novo Jogo</button>
</template>

<script>
export default {
	methods:{
		newGameClicado(){
      this.$emit('newGameAcionado');
    }
	}
}
</script>

<style>
	.buttonNewGame {
  display: inline-block;
  font-size: 16px;
  color: white;
  background-color: #007BFF;
  padding: 20px 30px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
	margin-top: 40px;
  text-decoration: none;
  transition: background-color 0.3s ease;
}

.buttonNewGame:hover {
  background-color: #0056b3;
}
</style>