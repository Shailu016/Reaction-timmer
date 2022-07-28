<template>
  <div>
    <h3>Reaction Time: {{ score }} ms</h3>
    <P class="rank">{{ rank }}</P>
  </div>
</template>
<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: 0,
    };
  },
  mounted() {
    if (this.score < 200) {
      this.rank = "Master Assassin";
    } else if (this.score < 300) {
      this.rank = "Fast as a Ninja";
    } else if (this.score < 400) {
      this.rank = "Slow as a Turtle";
    } else {
      this.rank = "You are a Sloth";
    }
  },
};
</script>

<style>
.rank {
  color: rgb(38, 173, 167);
  font-size: 1.4rem;
  font-weight: bold;
}
</style>;
