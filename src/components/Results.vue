<template>
  <div class="container">
    <p>Vuection Time: {{ score }} ms</p>
    <p>{{ rank }}</p>
  </div>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Wow! That was quick.';
    } else if (this.score < 400) {
      this.rank = 'Not bad not bad...';
    } else {
      this.rank = 'Turtle is faster than you.';
    }
  },
};
</script>

<style scoped>
.container {
  margin-top: 40px;
}
</style>
