<template>
  <div class="block" @click="stopTimer" v-if="showBlock">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
      //   console.log(this.delay);
    }, this.delay);
    console.log("mounted");
  },
  //   updated() {
  //     console.log("updated");
  //   },

  //   unmounted() {},

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  width: 200px;
  padding: 100px;
  border-radius: 10px;
  margin: 100px auto;
  background: rgb(6, 175, 96);
  color: #fff;
}
</style>
