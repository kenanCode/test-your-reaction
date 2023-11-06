<template>
<p> Reaction Time: {{  score }} ms</p>
<p class="rank"> {{  rank }} </p>
</template>

<script>
export default {
props: ['score'],
data () {
  return {
    rank: null
  }
},
mounted() {
  if (this.score < 250) {
    this.rank = "You're a Supersonic Energizer Bunny!"
  } else if (this.score < 400) {
    this.rank = "You're not bad, just like a duck in flight!"
  } else {
    this.rank = "You're a froggy sluggy snail!"
  }
 }
}
</script>

<style>
p{
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  color: rgb(100, 100, 208);
}

.rank {
  font-size: 1.6em;
  color: rgb(100, 100, 208);
}
</style>