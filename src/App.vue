<template>
  <h1 class="mt-8 text-center text-6xl text-fuchsia-700">
    Epiq Reaction Timer
  </h1>
  <button
    :disabled="isPlaying"
    class="my-4 w-20 rounded-2xl border bg-green-300 py-4 font-bold"
    @click="start"
  >
    Play
  </button>
  <block v-if="isPlaying" :delay="delay" @reaction-time="endGame" />
  <results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      // Generate a random delay between 2 and 7 seconds
      this.delay = 2000 + Math.round(Math.random() * 5000);
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>
<style scoped></style>
