<template>
  <div class="box" v-if="showBox" @click="stopTimer">click</div>
  {{ reactionTime }}
</template>
<script>
export default {
  name: "BoxReaction",
  props: ["delay"],
  data() {
    return {
      showBox: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBox = true;
      this.startTimer();
    }, this.delay);
  },
  //   updated() {
  //     console.log("updated");
  //   },
  //   unmounted() {
  //     console.log("unmounted");
  //   },
  methods: {
    startTimer() {
      this.timer = setInterval(() => (this.reactionTime += 1), 1);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.showBox = !this.showBox;
      console.log(this.reactionTime);
    },
  },
};
</script>

<style scoped>
.box {
  width: 40%;

  background: #f36932;

  text-align: center;
  color: #fff;

  padding: 90px 0;

  border-radius: 5px;

  margin-top: 40px;
}
</style>