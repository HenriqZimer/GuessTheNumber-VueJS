<template>
    <div id="gameArea">

        <div>
          <h3 id="textOutput">Your Guess:</h3>
          
        </div>

        <div class="stats">
          <div class="info">
            <p id="textOutput">{{ textOutput }}</p>
            <p>Number of attempts:</p>
            <span id="attempts">{{ attempts }}</span>
          </div>
          <div class="info">
            <p>Your guesses:</p>
            <span id="guesses">Guesses: {{ userNumbers }}</span>
          </div>
        </div>

      </div>
</template>

<script>
export default {
data() {
  return {
    computerNumber: 0,
    userNumber: null,
    userNumbers: [],
    attempts: 0,
    maxGuesses: 10,
    btnGame: false
  }
},
computed: {
    
    isGameOver() {
        return this.attempts >= this.maxGuesses || this.userNumber === this.computerNumber;
    }
},
methods: {
    textOutput() {
        if (this.attempts >= this.maxGuesses) {
            return 'You have reached the maximum number of attempts ' + this.computerNumber;
        } else if (this.userNumber == this.computerNumber) {
            this.btnGame = true;
            return 'Your number is correct';
        } else if (this.userNumber > this.computerNumber) {
            return 'Your number is too high';
        } else {
            return 'Your number is too low';
        }
    },
    newGame() {
        this.userNumber = null;
        this.userNumbers = [];
        this.attempts = 0;
        this.computerNumber = Math.floor(Math.random() * 100 + 1);
        console.log(this.computerNumber);
    },
    compareNumbers() {
        if (this.userNumber === null) {
    return; // Evita que o input seja limpo ao iniciar o jogo
        }
        this.userNumbers.push(' ' + this.userNumber);
        this.userNumber = null;

        if (this.attempts < this.maxGuesses && this.userNumber !== this.computerNumber) {
    this.attempts++;
        }
    }
},
    mounted() {
        this.newGame();
}
}
</script>

<style>

</style>