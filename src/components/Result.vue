<template>
  <p>Reaction Time : {{ score }}</p>
  <p class="rank">{{rank}}</p>
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
      this.rank = "Excellent";
    } else if (this.score < 400) {
      this.rank = "Great";
    } else {
      this.rank = "Nice";
    }
  },
};
</script>

<style>
.rank{
    margin: auto;
    padding: 8px;
    width: 200px;
    color: white;
    font-size: 1rem;
    font-weight: bold;
    background-color: #0984e3;
}</style>
