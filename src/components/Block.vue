<template>
  <div class="block" v-if="showBlock" @click="stopTimer"> CLICK </div>
</template>

<script>
export default {
props: ['delay'],
data() {
  return {
    showBlock: false,
    timer: null,
    reactionTime: 0
  }
},
mounted () {
  setTimeout(() => {
    this.showBlock = true
    this.startTimer()
  }, this.delay)
},
methods: {
  startTimer() {
  this.timer = setInterval(() => {
    this.reactionTime += 10
}, 10)
  },
  stopTimer() {
   clearInterval(this.timer)
   this.$emit('endPlay', this.reactionTime)
  }
 }
}
</script>

<style>
.block{
  width: 200px;
  height: 200px;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-size: 1.1em;
  border-radius: 20px;
  background-color: rgb(100, 100, 208);
  margin: 40px auto;
}

</style>