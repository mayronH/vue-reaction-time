<script setup lang="ts">
import { onMounted, ref } from 'vue'

const props = defineProps({
  delay: {
    type: Number,
    required: true,
  },
})

const showBox = ref(false)
const startTime = ref()
const timeout = ref()
const reactionTime = ref(0)

onMounted(() => {
  timeout.value = setTimeout(() => {
    showBox.value = true
    startTimer()
  }, props.delay)
})

const emit = defineEmits(['endGame'])
const emitEndGame = () => {
  emit('endGame', reactionTime.value)
}

function startTimer() {
  startTime.value = Date.now()
}

function stopTimer() {
  reactionTime.value = Date.now()
  reactionTime.value = reactionTime.value - startTime.value
  emitEndGame()
}
function handleMissClick() {
  clearTimeout(timeout.value)
  reactionTime.value = -1
  emitEndGame()
}
</script>

<template>
  <div class="tooFast" @click.self="handleMissClick">
    <div class="box" v-if="showBox" @click="stopTimer">click</div>
  </div>
</template>

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

  background: var(--accent);

  text-align: center;
  color: var(--white);

  padding: 90px 0;
  margin: auto;

  border-radius: 5px;
}
</style>
