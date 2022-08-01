  <template>
  <div class="container">
    <h1>Reaction Timmer</h1>
    <button class="button" @click="start" :disabled="isPlaying">
      Let's get started
    </button>
    <Result v-if="showRersults" :score="score" />
    <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  </div>
</template>

  <script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
      showRersults: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showRersults = false;
    },
    endGame(reactionTime) {
      this.isPlaying = false;
      this.score = reactionTime;
      this.showRersults = true;
    },
  },
};
</script>

  <style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
@media only screen and (max-width: 768px) {
  .container {
    margin-top: 90px;
    width: 100%;
  }
}

button {
  background-color: rgb(38, 173, 167);
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  font-size: 1.2rem;
  cursor: pointer;
  margin-top: 20px;
}
button[disabled] {
  background-color: #ccc;
  cursor: not-allowed;
}
</style>
