<template>
  <!--Start Stop-->
  <div
    :class="{
      boxStop: gameStart,
      boxStart: gameStop,
    }"
  >
    <go
      class="goBtn"
      @close="startGame"
      :delay="delay"
      :isStart="isStart"
      :gameStart="gameStart"
      :gameStop="gameStop"
      @open="stopGame"
    >
    </go>
    <result
      class="resultView"
      :score="score"
      :highScore="highScore"
      :isStart="isStart"
      :earlyTime="earlyTime"
    ></result>
  </div>
</template>

<script>
import go from "./components/Go.vue";
import result from "./components/Result.vue";
export default {
  name: "App",
  data() {
    return {
      gameStop: true,
      gameStart: false,
      delay: 5000,
      time: null,
      reactionTime: 0,
      score: 0,
      isStart: false,
      highScore: "0",
      class: null,
      earlyTime: false,
    };
  },
  components: {
    go,
    result,
  },
  methods: {
    startGame() {
      this.class = setTimeout(() => {
        this.startTimer();
        this.gameStart = true;
        this.gameStop = false;
        this.early = true;
      }, this.delay);
      this.isStart = !this.isStart;
      this.reactionTime = 0;
    },
    startTimer() {
      this.time = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopGame() {
      clearTimeout(this.class);
      clearInterval(this.time);
      this.gameStart = false;
      this.gameStop = true;
      this.score = this.reactionTime / 1000;
      this.isStart = !this.isStart;
      if (this.highScore == 0) {
        this.highScore = this.score;
      }
      if (this.highScore > this.score && this.Score > 0) {
        this.highScore = this.score;
      }
      if (this.reactionTime == 0) {
        this.earlyTime = true;
      }
    },
  },
};
</script>


<style >
.boxStart {
  width: 100%;
  height: 100vh;
  background-color: #42adf5;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.boxStop {
  width: 100%;
  height: 100vh;
  background-color: green;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.goBtn {
  margin-top: 10%;
}
.resultView {
  margin-top: 20px;
}
</style>
