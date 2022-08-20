<script>
import Results from './components/Results.vue';
import Shape from './components/Shape.vue';
export default {
  name: 'App',
  components: {
    Shape,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      isPunished: false,
      delay: null,
      score: null,
      showVuection: false,
    };
  },
  methods: {
    startGame() {
      this.delay = 1000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showVuection = false;
    },
    endGame(vuectionTime) {
      this.score = vuectionTime;
      this.isPlaying = false;
      this.showVuection = true;
      this.isPunished = false;
    },
    punishPlayer() {
      this.isPlaying = false;
      this.isPunished = true;
      alert("Please don't random click!");
    },
  },
};
</script>

<template>
  <div class="punish-bg" @click.self="punishPlayer">
    <h1>Vuection</h1>
    <button class="playButton" @click="startGame" :disabled="isPlaying">
      PLAY
    </button>
    <Shape v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results v-if="showVuection" :score="score" />
  </div>
</template>

<style scoped>
.playButton {
  width: 120px;
  height: 40px;
  margin-top: 2rem;
  cursor: pointer;
}
.playButton[disabled] {
  cursor: not-allowed;
}
.punish-bg {
  top: 0;
  position: fixed;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
</style>
