<template>
    <div class="result">
        <h2>
            <span v-if="score < 0"> Too soon, try again </span>
            <span v-else>
                Reaction time: <span class="score">{{ score }} ms</span>
            </span>
        </h2>
    </div>
</template>
<script>
export default {
    name: "ResultReaction",
    props: ["score"],
};
</script>
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
