<template>
  <div class="stopwatch-container">
    <span class="addStopwatch" @click="addStopwatch"><font-awesome-icon icon="fa-solid fa-plus" /></span>
    <span class="clock">{{clock}}</span>
    <div class="bottom-button">
      <div class="play-stop">
        <span class="stop" v-if="!this.playStop" @:click="stopStopwatch"><font-awesome-icon icon="fa-solid fa-pause" /> </span>
        <span class="start" v-if="this.playStop" @:click="startStopwatch"><font-awesome-icon icon="fa-solid fa-play" /> </span>
      </div>
      <span class="clear" @:click="clearStopwatch"><font-awesome-icon icon="fa-solid fa-square" /></span>
    </div>
  </div>
</template>

<script>

export default {
  name: 'stopwatchComp',
  data(){
    return{
      secunds:0,
      interval:null,
      playStop:true,
    }
  },
  methods:{
    addStopwatch(){
      this.$root.countStopwatch++;
    },
    startStopwatch(){
      this.stopStopwatch()
      this.interval = setInterval(()=>{
        this.secunds++;
      },1000)
    },
    stopStopwatch(){
      clearInterval(this.interval);
      this.playStop = !this.playStop
    },
    clearStopwatch(){
      this.stopStopwatch();
      this.playStop = !this.playStop;
      this.secunds = 0; 
    }
  },
  computed:{
    clock:function(){
      let secunds = this.secunds%60;
      let minutes = Math.floor(Math.floor(this.secunds/60)%60);
      let hours = Math.floor(Math.floor(this.secunds/60)/60);

      let result = secunds

      if(minutes){
        result = minutes + ":" + result
      }
      if(hours){
        result = hours + ":" + result
      }
      return result;
    }
  },
  created(){
    this.startStopwatch()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style lang="sass">
.stopwatch-container
  width: 400px
  height: 150px
  font-size: 40px
  background-color: #464646
  padding: 10px 20px
  display: flex
  flex-direction: column
  justify-content: space-between
  margin: 15px
  border-radius: 10px
.play-stop
  margin-right: 10px
  width: 40px
.bottom-button
  display: flex
.clock
  display: flex
  justify-content: center
.addStopwatch
  display: flex
  justify-content: end
</style>
