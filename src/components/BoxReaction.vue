<template>
  <div class="box">click</div>
</template>
<script>
export default {
  name: "BoxReaction",
  props: ["delay"],
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