<template>
  <div id="app">
    <img class="logo" src="./assets/logo.svg">
    <h1 class="name"> Julian Ludwig </h1>
    <div class="clock">{{clock}}</div>
   <!-- <fact-sheet-types/> -->
  </div>
</template>

<script>
import FactSheetTypes from './components/FactSheetTypes'

export default {
  name: 'App',
  components: {
    FactSheetTypes
  },
  data () {
    return {
      clock: this.updateclock()
    }
  },
  methods: {
    updateclock () {
      return new Date().toISOString()
    }
  },
  mounted () {
    setInterval(() => {
      this.clock = this.updateclock()
    }, 1000)
    this.$lx.init()
      .then(setup => {
        this.$lx.ready({})
      })
  }
}
</script>

<style lang="stylus" scoped>
  @import './stylus/main'

  .clock
    font-size 64px

  .name
    color blue
    font-size 126px

  #app
    display flex
    flex-flow column
    justify-content center
    align-items center

  .logo
    width 250px
    margin 2rem
    align-self flex-end
</style>
