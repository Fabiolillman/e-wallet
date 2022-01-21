<template>
  <div class="card-wrapper">
    <div class="img-container">
    <img src="../assets/wifi.svg" alt="">
     <img src="../assets/evil.svg" alt="">
     </div>
      <img src="../assets/chip.svg" alt="">
      <p>{{cardInfo.CCV}}</p>
      <div class="wrapper-card-text">
      <!-- <label for="" >CARDHOLDER NAME</label> -->
      <label for="">{{spacedNumbers}}</label>
      </div>
      <div class="wrapper-card-text2">
      <!-- <label for=""> {{cardInfo.cardNumber}} </label> -->
      <label for="">CARDHOLDER</label>
      <label for="">VALID THROUGH</label>
      </div>
     
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
.card-wrapper{
 border-radius: 10px;
 width: 23.875rem;
 height: 15.063rem;
 background-color: #D0D0D0;
 margin: 0 1rem 0 1rem;
 padding: 0 1rem 0 1rem;
 box-sizing: border-box;
 text-align: start ;
}

.img-container{
  display: flex;
  justify-content: space-between;
  /* margin: 0 1rem 0 1rem; */
}

.wrapper-card-text2{
  display: flex;
  justify-content: space-between;
}



</style>