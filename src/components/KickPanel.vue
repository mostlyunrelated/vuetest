<template> 
 <div> 
  <button @click="kick">kick</button> 
  <p v-if="kicks > 0">Kicks generated: {{ kicks }}</p> 
 </div> 
</template> 

<script> 

 export default { 
  data() { 
   return { 

   } 
  }, 
 methods: { 
  kick() { 
   this.$emit('add-kick'); 
  }
 },
 props: { 
  kicks: {  
   required: true 
   } 
  } 
 } 
</script> 
