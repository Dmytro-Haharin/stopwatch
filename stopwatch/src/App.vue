<template>
  
  <div class="stopwatchComp-container"  >
    <stopwatchComp v-for="n in countStopwatch"/>
  </div>
</template>

<script>
import stopwatchComp from './components/stopwatchComp.vue'

export default {
  name: 'App',
  components: {
    stopwatchComp,
    
  },
  data(){
    return{
      countStopwatch:1,
    }
  }
}
</script>

<style lang="sass">
body
  background: #6f6f6f


  .stopwatchComp-container
    display: flex
    flex-wrap: wrap
  </style>
