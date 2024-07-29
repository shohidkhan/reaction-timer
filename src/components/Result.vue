<template>
  <p>Reaction Time: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Excellent...";
    } else if (this.score > 250 && this.score < 400) {
      this.rank = "Pretty Good...";
    } else if (this.score > 400 && this.score < 800) {
      this.rank = "Not Bad...";
    } else {
      this.rank = "You are Too slow...";
    }
  },
};
</script>

<style scoped>
.rank {
  color: rgb(6, 175, 96);
  font-size: 1.4em;
  font-weight: bold;
}
</style>
