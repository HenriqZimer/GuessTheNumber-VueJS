<template>
  <div class="input">
    <input type="number" v-model="numeroJogado" @change="inputClicado">
    <div>
      <div v-if="tentativas >= 1">
      <h2 v-if="ultimaJogada > numeroRandom">Ta alto</h2>
      <h2 v-else>Ta Baixo</h2>
      </div>
      <h3>Suas Tentativas:</h3>
      <h5> {{ numerosJogados }}</h5>
      <h3>Numero de Tentativas:</h3>
      <h5> {{ tentativas }}</h5>
    </div>
  </div>
</template>

<script>
export default {
  props: ['numeroRandom'],
  data() {
    return {
      numeroJogado: null,
      numerosJogados: [],
      tentativas: 0,
      ultimaJogada: 0,
    }
  },
  methods: {
    resultadosArray() {
      this.numerosJogados.push(this.numeroJogado);
      this.numeroJogado = '';
      this.tentativas++;
    },
    removeUltimo(){
      let jogadas = this.numerosJogados.slice(0)
      this.ultimaJogada = jogadas.pop()
    },
    inputClicado() {
      this.resultadosArray() 
      this.removeUltimo()
      this.$emit('inputAcionado', this.tentativas, this.numerosJogados, this.numeroJogado, this.ultimaJogada)
    }
  }
}
</script>

<style>
  .input {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    flex-direction: column;
    text-align:center
  }
  
</style>