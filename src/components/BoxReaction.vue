<template>
  <div class="tooFast" @click.self="handleMissClick">
    <div class="box" v-if="showBox" @click="stopTimer">click</div>
  </div>
</template>
<script>
export default {
  name: "BoxReaction",
  props: ["delay", "onGame"],
  data() {
    return {
      showBox: false,
      startTime: null,
      timeout: null,
      reactionTime: 0,
    };
  },
  mounted() {
    this.timeout = setTimeout(() => {
      this.showBox = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    emitEndGame() {
      this.$emit("endGame", this.reactionTime);
    },
    startTimer() {
      this.startTime = Date.now();
    },
    stopTimer() {
      this.reactionTime = Date.now();
      this.reactionTime = this.reactionTime - this.startTime;
      this.emitEndGame();
    },
    handleMissClick() {
      clearTimeout(this.timeout);
      this.reactionTime = -1;
      this.emitEndGame();
    },
  },
};
</script>

<style scoped>
.tooFast {
  width: 100%;
  min-height: 200px;

  padding-top: 40px;

  display: flex;
  justify-content: center;
  align-items: center;
}
.box {
  width: 40%;

  background: #f36932;

  text-align: center;
  color: #fff;

  padding: 90px 0;
  margin: auto;

  border-radius: 5px;
}
</style>