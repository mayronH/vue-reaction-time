<template>
  <main>
    <h1>Reaction Timer</h1>
    <p>Click on the button to start the game</p>
    <button @click="startGame" class="button" :disabled="onGame">play</button>
    <p v-show="onGame">
      A box will appear at random, try to click on it the faster as you can
    </p>
    <BoxReaction v-if="onGame" :delay="delay" />
  </main>
</template>

<script>
import BoxReaction from "./components/BoxReaction.vue";

export default {
  name: "App",
  components: { BoxReaction },
  data() {
    return {
      onGame: false,
      delay: null,
    };
  },
  methods: {
    startGame() {
      // Delay between 2s and 7s
      this.delay = 1000 + Math.random() * 5000;
      this.onGame = true;
    },
  },
};
</script>

<style>
#app {
  height: 100%;
}

main {
  display: flex;
  flex-direction: column;
  align-items: center;

  max-width: 960px;

  margin: auto;

  padding-top: 80px;
}

h1 {
  margin-bottom: 1rem;
}

.button {
  min-width: 120px;

  padding: 0.5rem 1.15rem;

  border: none;
  border-radius: 5px;

  background-color: #f36932;
  color: #fff;
  font-size: 18px;

  margin: 25px 0;

  box-shadow: 5px 5px 5px 0px rgba(0, 0, 0, 0.2);
}

.button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
