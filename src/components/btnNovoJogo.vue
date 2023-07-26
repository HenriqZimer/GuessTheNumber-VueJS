<template>
	<button @click="newGameClicado">Novo Jogo</button>
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

</style>