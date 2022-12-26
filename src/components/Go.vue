<template>
  <button
    @click.prevent.capture="$emit('close')"
    class="start"
    v-show="!isStart"
  >
    Start
  </button>
  <button @click.prevent.capture="$emit('open')" class="stop" v-show="isStart">
    Stop
  </button>
</template>

<script>
export default {
  name: "go",
  data() {
    return {};
  },
  emits: ["close", "open"],
  props: ["delay", "isStart", "gameStart", "gameStop"],
};
</script>


<style scoped>
.start {
  width: 500px;
  height: 150px;
  border: none;
  border-radius: 20px;
  background-color: green;
  margin-top: 13%;
  color: white;
  font-size: 40px;
  align-items: center;
  cursor: pointer;
}
.stop {
  width: 500px;
  height: 150px;
  border: none;
  border-radius: 20px;
  background-color: red;
  margin-top: 13%;
  color: white;
  cursor: pointer;
  font-size: 40px;
  align-items: center;
}
</style>
