<template>
  <div
    v-if="showBlock"
    class="m-10 mx-auto w-300 rounded-2xl border bg-red-800 py-24 px-0 text-center text-xl text-white"
    @click="stopTImer"
  >
    Click Me
  </div>
</template>
<script>
export default {
  props: ["delay"],
  emits: ["reaction-time"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },

  // lifeCycle hooks
  // fires off when the component is created
  mounted() {
    console.log("mounted component");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    // start as the button appears
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTImer() {
      clearInterval(this.timer);
      // emit event
      this.$emit("reaction-time", this.reactionTime);
    },
  },
  // // fires off when the component is updated
  // updated() {
  //   console.log("updated component");
  // },
  // // fires off when the component is destroyed
  // unmounted() {
  //   console.log("unmounted component");
  // },
};
</script>
<style lang=""></style>
