<template>
  <h1>BD Timer Reaction</h1>
  <button @click="start" :class="{ disab: isPlaying }" :disabled="isPlaying">
    Play
  </button>
  <Result v-if="showResult" :score="score"></Result>
  <BLock v-if="isPlaying" :delay="delay" @end="endGame"></BLock>
</template>

<script>
import BLock from "./components/BLock.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: {
    BLock,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.showResult = false;
      this.delay = 2000 + Math.random() * 5000;
    },
    endGame(reacTime) {
      console.log(reacTime);
      this.score = reacTime;
      this.showResult = true;
      this.isPlaying = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  background: rgb(26, 155, 26);
  outline: 0;
  border: 0;
  border-radius: 5px;
  padding: 5px 15px;
  color: #fff;
  cursor: pointer;
}
.disab {
  background: rgba(26, 155, 26, 0.4);
  cursor: not-allowed;
}
</style>
