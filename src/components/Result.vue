<template>
  <div class="result">
    <template v-if="!isStart">
      <div class="score" v-if="earlyTime">
        <h2 v-if="score > 0">Your score is {{ score }}</h2>
        <h2 v-else>Too Early</h2>
      </div>
      <h2 class="score" v-else>Start the Game</h2>
    </template>
    <template v-else-if="isStart">
      <h2 class="score">Stop when the color changes</h2>
    </template>
    <div class="highScore">
      <h3>Your high score is:</h3>
      <h4>{{ highScore }} sec</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: "result",
  data() {
    return {
      score: 0,
      highScore: 0,
    };
  },
  methods: {},
  props: ["score", "highScore", "isStart", "earlyTime"],
};
</script>


<style scoped>
.result {
  width: 500px;
  height: 150px;
  border: none;
  border-radius: 20px;
  background-color: #dff0f2;
  color: grey;
  font-size: 15px;
}
.score {
  margin-left: 20px;
  margin-top: 15px;
}
.highScore {
  margin-top: 40px;
  margin-left: 20px;
}
</style>