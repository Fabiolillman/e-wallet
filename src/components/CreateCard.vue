<template>
  <div card>
    <img src="" alt="">
     <img src="" alt="">
      <img src="" alt="">
      <p>{{cardInfo.CCV}}</p>
      <div class="wrapper-card-text">
      <label for="" >CARDHOLDER NAME</label>
      <label for="">{{spacedNumbers}}</label>
      </div>
      <div class="wrapper-card-text2">
      <label for=""> {{cardInfo.cardNumber}} </label>
      <label for=""></label>
      </div>
       <button @click='call'>Testing</button>
      </div>
</template>

<script>
export default {
props:[
  'cardInfo'
],

computed:{
//  fullYear(){
// //    this.cardInfo.cardholder.split(' ').toUpperCase()
// //  {{firstName}} + " " {{lastName}}
//  } 
 spacedNumbers(){
   let space=""
   for (let i = 0; i < this.cardInfo.cardNumber.length; i++) {
       if (i % 4 == 0) {
            space += " ";
        }
        // else if (space.length===16){
    
        // }
        space+=this.cardInfo.cardNumber[i]
   }
  return space
 }

},

methods:{
  
  call(){
    // console.log(this.cardInfo.CCV)
    if (this.cardInfo.cardNumber.length > 0) {

        if (this.cardInfo.cardNumber.length % 4 == 0) {
            this.cardInfo.cardNumber.length += " ";
        }
    }
  },
  
}  
}
</script>

<style scoped>



</style>