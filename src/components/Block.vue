<template>
  <div class="block" v-if="showBlock" @click="stopTimmer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timmer: null,
      reactionTime: 0,
    };
  },

  mounted() {
    console.log("component mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimmer();
      console.log(this.delay);
    }, this.delay);
  },

  methods: {
    startTimmer() {
      this.timmer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimmer() {
      clearInterval(this.timmer);
      console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 40px auto;
  width: 600px;
  height: 400px;
  background-color: #444;
  border-radius: 10px;
  color: #fff;
  font-size: 20px;
  font-weight: bold;
  text-align: center;
  line-height: 100px;
  cursor: pointer;
}
.block:hover {
  animation: shake 0.2s;
  animation-iteration-count: infinite;
}

@keyframes shake {
  0% {
    transform: translate(1px, 1px) rotate(0deg);
  }
  10% {
    transform: translate(-1px, -2px) rotate(-1deg);
  }
  20% {
    transform: translate(-3px, 0px) rotate(1deg);
  }
  30% {
    transform: translate(3px, 2px) rotate(0deg);
  }
  40% {
    transform: translate(1px, -1px) rotate(1deg);
  }
  50% {
    transform: translate(-1px, 2px) rotate(-1deg);
  }
  60% {
    transform: translate(-3px, 1px) rotate(0deg);
  }
  70% {
    transform: translate(3px, 1px) rotate(-1deg);
  }
  80% {
    transform: translate(-1px, -1px) rotate(1deg);
  }
  90% {
    transform: translate(1px, 2px) rotate(0deg);
  }
  100% {
    transform: translate(1px, -2px) rotate(-1deg);
  }
}
@media only screen and (max-width: 768px) {
  .block {
    width: 300px;
    height: 200px;
    line-height: 50px;
  }
}
</style>