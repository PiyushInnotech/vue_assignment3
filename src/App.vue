<template>
  <!--Start Stop-->
  <div :class="isClass ? 'boxStop' : 'boxStart'">
    <Go
      class="goBtn"
      @close="timer"
      :delay="delay"
      :isStart="isStart"
      :isClass="isClass"
      @open="stopTimer"
    >
    </Go>
    <Result
      class="resultView"
      :score="score"
      :highScore="highScore"
      :reactionTime="reactionTime"
      :isStart="isStart"
    ></Result>
  </div>
</template>

<script>
import Go from "./components/Go.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  data() {
    return {
      isClass: false,
      delay: 5000,
      time: null,
      reactionTime: 0,
      score: 0,
      isStart: false,
      highScore: '0',
    };
  },
  components: {
    Go,
    Result,
  },
  methods: {
    timer() {
      setTimeout(() => {
        this.startTimer();
        this.isClass = true;
      }, this.delay);
      this.isStart = !this.isStart;
    },
    startTimer() {
      this.time = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.time, this.timer);
      this.isClass = !this.isClass;
      this.score = this.reactionTime / 1000;
      this.isStart = !this.isStart;
      if (this.highScore == 0) {
        this.highScore = this.score
      }
      if(this.highScore>this.score){
        this.highScore = this.score
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
