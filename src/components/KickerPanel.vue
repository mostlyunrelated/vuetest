<template>
 <div v-if="kicks >= 10 || kickers > 0">
   <button @click="buyKicker(1)">buy a kicker for {{ kickerPrice }} kicks</button>
   <p v-if="kickers >0">Kickers owned: {{ kickers }} with generation rate: {{ kickers*kickerRate }}/sec </p>
 </div>
</template>

<script>

 export default {
  data() {
   return {
    kickerPrice: 10
   }
  },
 methods: {
  buyKicker(quantity) {
   if (quantity === 0) {return;}
   var finalPrice = this.kickerPrice * quantity;
   if (this.kicks >= finalPrice) {
    this.kickerPrice = Math.round(this.kickerPrice * 1.2);
    this.$emit('add-kicker', quantity, finalPrice);
   }
  }
 },
 props: { 
  kicks: {  
   required: true 
   },
  kickers: {
   required: true
   },
  kickerRate: {
   required: true
   }
  }
 }
</script>
