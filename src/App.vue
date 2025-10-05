<template>
  <h1>{{ title }}</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <block v-if="isPlaying" :delay="delay" @end="endGame" />
  <p>Reaction time: {{ score }} ms</p>
</template>

<script>
import Block from "./components/Block.vue";

export default {
  name: "App",
  components: { Block },
  data() {
    return {
      title: "Bartah Reaction Timer",
      isPlaying: false,
      delay: null,
      score: null,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
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
  margin: 60px;
}
/* button {
  background: green;
  color: white;
  width: 70px;
  padding: 10px;
  border-radius: 10px;
  border: none;
  font-weight: bold;
  cursor: pointer; 
} */
</style>
