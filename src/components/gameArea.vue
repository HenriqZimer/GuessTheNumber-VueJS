<template>
    <div id="gameArea">

        <section>
          <h3 id="textOutput">Your Guess:</h3>
          <input type="number" v-model="userNumber" @input="compareNumbers"/>
        </section>

        <section class="stats">
          <div class="info">
            <p id="textOutput">{{ textOutput }}</p>
            <p>Number of attempts:</p>
            <span id="attempts">{{ attempts }}</span>
          </div>
          <div class="info">
            <p>Your guesses:</p>
            <span id="guesses">Guesses: {{ userNumbers }}</span>
          </div>
        </section>

        <button id="newGameButton" @click="newGame()">NEW GAME</button>

      </div>
</template>

<script>
export default {
data() {
    return {
    textOutput: '',
    userNumber: null,
    userNumbers: [],
    attempts: 0,
    maxGuesses: 10,
    computerNumber: Math.floor(Math.random() * 100) + 1
    }
},
methods: {
    newGame() {
        window.location.reload()
    },
    methods: {
                compareNumbers() {
                    this.userNumbers.push(' ' + this.userNumber);

                    if (this.attempts < this.maxGuesses) {
                        if (this.userNumber > this.computerNumber) {
                            this.textOutput = 'Your number is too high';
                        } else if (this.userNumber < this.computerNumber) {
                            this.textOutput = 'Your number is too low';
                        } else {
                            this.textOutput = 'Your number is correct';
                            this.$refs.inputBox.setAttribute('readonly', 'readonly');
                        }

                        this.userNumber = null;
                        this.attempts++;
                    } else {
                        this.textOutput = 'You have reached the maximum number of attempts. The correct number was: ' + this.computerNumber;
                        this.$refs.inputBox.setAttribute('readonly', 'readonly');
                    }
                }
}
}
}

</script>

<style>

</style>