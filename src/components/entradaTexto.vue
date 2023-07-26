<template>
  <div class="input">
    <!-- <input type="number" v-model="numeroJogado" @change="inputClicado"> -->
    <input type="number" v-model="numeroJogado" @change="chamarMethodos">
    <ul>
      <li>Suas Tentativas: {{  }} </li>
      <h5 style="text-align:center"> {{ numerosJogados }}</h5>
      <li>Numero de Tentativas:</li>
      <h5 style="text-align:center"> {{ tentativas }}</h5>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numeroJogado: null,
      numerosJogados: [],
      tentativas: 0,
      ultimoResultado: 0
    }
  },
  methods: {
    chamarMethodos(){
      this.resultadosArray() 
      this.removeUltimo()
      this.inputClicado()
    },
    resultadosArray () {
      this.numerosJogados.push(this.numeroJogado);
      this.numeroJogado = '';
      this.tentativas++;
    },
    removeUltimo(){
      this.ultimoResultado = this.myArray.pop();
      console.log(this.ultimoResultado); // Isto irá imprimir o último elemento removido
      // console.log(this.numerosJogados);
    },
    inputClicado() {
      this.$emit('inputAcionado', this.tentativas, this.numerosJogados, this.numeroJogado)
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
  }
  
</style>