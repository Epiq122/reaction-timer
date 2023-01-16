<template>
  <p>Reaction time - {{ score }} MS</p>
  <p class="text text-2xl font-bold text-red-200">Rank - {{ rank }}</p>
</template>

<script>
export default {
  name: "Results",
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Amazing";
    } else if (this.score < 500) {
      this.rank = "Good";
    } else if (this.score < 1000) {
      this.rank = "Average";
    } else {
      this.rank = "Poor";
    }
  },
};
</script>

<style></style>
