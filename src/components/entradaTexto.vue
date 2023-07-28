<template>
  <div class="input">
      <div v-if="tentativas >= 1">
      <h2 v-if="ultimaJogada > numeroRandom" style="color: red">Você jogou Alto</h2>
      <h2 v-else style="color: blue">Você jogou Baixo</h2>
      </div>
    <input type="number" v-model="numeroJogado" @change="inputClicado">
    <div>
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
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 70px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
  margin-bottom: 20px;
  width: 500px;
  text-align: center;
}

.input h2 {
  font-size: 30px;
  color: #333;
  margin: -45px 0;
}

.input input {
  width: 50%;
  padding: 10px;
  font-size: 18px;
  border-radius: 5px;
  border: 1px solid #ccc;
  margin-bottom: 20px;
  text-align: center;
}

.input h3 {
  font-size: 20px;
  color: #333;
  margin-bottom: 10px;
}

.input h5 {
  font-size: 14px;
  color: #666;
  margin-bottom: 20px;
}
</style>