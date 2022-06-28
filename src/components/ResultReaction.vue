<script setup lang="ts">
const props = defineProps({
  score: {
    type: Number,
    required: true,
  },
})
</script>

<template>
  <div class="result">
    <h2>
      <span v-if="props.score < 0"> Too soon, try again </span>
      <span v-else>
        Reaction time: <span class="score">{{ props.score }} ms</span>
      </span>
    </h2>
  </div>
</template>

<style scoped>
h2 {
  margin-top: 60px;
}
.score {
  font-weight: 400;
  font-size: 40px;
  color: var(--accent);
}
</style>
