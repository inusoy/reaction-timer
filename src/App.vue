<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <GameDescription />
  <ReflexButton ref="reflexButton" @buttonPressed="controlGame" />
  <ResultsBlock v-if="result !== 0" :result=this.result />
</template>

<script>
import GameDescription from './components/GameDescription.vue';
import ReflexButton from './components/ReflexButton.vue';
import ResultsBlock from './components/ResultsBlock.vue';

export default {
  name: 'App',
  components: {
    GameDescription,
    ReflexButton,
    ResultsBlock
  },
  data() {
    return {
      timer: 0,
      result: 0,
      gameRunning: false,
      startingTime: 0,
    }
  },
  methods: {
    controlGame() {
      !this.gameRunning ? this.startGame() : this.endGame()
    },
    startGame() {
      this.toggleButton()
      this.gameRunning = true
      const timeout = this.getRandomInRange(2000, 5000)
      setTimeout(() => {
        this.toggleButton()
        this.startingTime = performance.now()
      }, timeout)
    },
    endGame() {
      this.result = performance.now() - this.startingTime
      this.toggleButton()
      this.gameRunning = false      
    },
    getRandomInRange(min, max) {
      return Math.random() * (max - min) + min;
    },
    toggleButton() { //done with chatGPT
      const reflexButtonComponent = this.$refs.reflexButton; // Accessing the ReflexButton component instance
      if (reflexButtonComponent) {
        reflexButtonComponent.toggleDisplay(); // Calling the toggleDisplay() method of the ReflexButton component
      }
    },

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
