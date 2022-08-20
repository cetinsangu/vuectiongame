<template>
  <div class="shape" v-if="showShape" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showShape: false,
      timer: null,
      vuectionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showShape = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.vuectionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit('end', this.vuectionTime);
    },
  },
};
</script>

<style>
.shape {
  width: 400px;
  border-radius: 20px;
  background: #fff;
  color: black;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
