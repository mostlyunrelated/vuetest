<template>
<html>

  <head>
    <title> OK PASHA </title>
  </head>

  <body>

    <div id="app">
      <p>Welcome to Kickie Klicker!</p>
      <KickPanel :kicks="kicks" @add-kick="addKick"></KickPanel>
      <KickerPanel :kicks="kicks" :kickers="kickers" :kickerRate="kickerRate" @add-kicker="addKicker"></KickerPanel>
    </div>
  </body>
</html>
</template>

<script>

import KickPanel from './components/KickPanel.vue'
import KickerPanel from './components/KickerPanel.vue'

export default {
  name: 'app',
  data() {
   return {
    kicks: 0,
    kickers: 0,
    kickerRate: 1
   }
  },
  components: {
    KickPanel,
    KickerPanel
  },
  methods: {
    addKick() {
	this.kicks += 1;
    },
    addKicker(quantity, finalPrice) {
     if (this.kickers === 0) {
        var genKPSID = setInterval(this.genKPS, 1000)
     }
     this.kickers += quantity;
     this.kicks -= finalPrice;
    },
    genKPS() {
     this.kicks += this.kickers * this.kickerRate;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
