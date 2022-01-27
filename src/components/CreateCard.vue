<template>
  <div class="card-wrapper"
  @click="$emit('click')"
  :style="{ 'background-color': backgroundColor() }" >
    <div class="img-container">
    <img src="../assets/wifi.svg" alt="">
     <img v-bind:src="imageSelect" 
     
     alt="">
     <!-- :style="{ 'background-color': currentColor }" -->
     <!-- <img src="../assets/evil.svg" alt=""> -->
     </div>
      <img src="../assets/chip.svg" alt="">
      <div class="wrapper-card-text">
      <!-- <label for="" >CARDHOLDER NAME</label> -->
      <label for="" class="number-label">{{spacedNumbers}}</label>
      <label for="" v-if="spacedNumbers.length<1">XXXX XXXX XXXX XXXX</label>
      </div>
      <div class="wrapper-card-text2">
      <!-- <label for=""> {{cardInfo.cardNumber}} </label> -->
      <label for="">CARDHOLDER</label>
      <label for="">VALID THROUGH</label>
      </div>
      <div class="wrapper-card-text2">
     
      <label for="">{{cardInfo.cardholder}}</label>
      <label for="">{{fullYear}}</label>
      
      </div>
     
      </div>
</template>

<script>
export default {

data(){return{
  currentImg:'',
  currentColor:'orange'
}},

props:[
  'cardInfo'
],



computed:{
 fullYear(){
 return this.cardInfo.expireMonth + " / " + this.cardInfo.expireYear
 },

  imageSelect(){
    if (this.cardInfo.vendor==="Ninja Corp") {
      return require('../assets/ninja.svg');
    } else  if (this.cardInfo.vendor==="Evil Corp") {
      return require('../assets/evil.svg');
    }  else  if (this.cardInfo.vendor==="Bitcoin Empire") {
      return require('../assets/bitcoin.svg');
    }  else  if (this.cardInfo.vendor==="Chain's Gains") {
      return require('../assets/blockchain.svg');
    } 
      //  <option>Ninja Corp</option>
      //     <option>Evil Corp</option>
      //     <option>Bitcoin Empire</option>     
      //     <option>Chain's Gains</option>
    // return require(`../assets/ ${ this.cardInfo.vendor}  .svg` ) 

   return "hello"
     },

 spacedNumbers(){

   let space=''
 
   for (let i = 0; i < this.cardInfo.cardNumber.length; i++) {
    
       if (i % 4 == 0) {
            space += " ";
        } 
      
        space+=this.cardInfo.cardNumber[i]
     
        if (space.length>19) {
          return space
        }
   }
  
      return space
    
 }
 
},

methods:{

  backgroundColor(){
    if (this.cardInfo.vendor==="Ninja Corp") {
      return "rgba(0,0,0,0.5)"   
    } else  if (this.cardInfo.vendor==="Evil Corp") {
      return this.currentColor="#F33355"   
    } else  if (this.cardInfo.vendor==="Bitcoin Empire") {
      return this.currentColor="#FFAE34"   
    } else  if (this.cardInfo.vendor==="Chain's Gains") {
      return this.currentColor="#8B58F9"   
    }    
  },

  // activateCard(){
  //  this.$emit('activateCard')
  // },
  // console(){
  //    console.log(this.cardInfo.CCV)
  // }
  // imageSelect(){
  //   if (this.carInfo.vendor=="Ninja Corp") {
  //     this.currentImg='../assets/evil.svg'
  //   }
  //    }
    //  <option>Ninja Corp</option>
    //       <option>Evil Corp</option>
    //       <option>Bitcoin Empire</option>     
    //       <option>Chain's Gains</option>
 
  // call(){
  //   // console.log(this.cardInfo.CCV)
  //   if (this.cardInfo.cardNumber.length > 0) {

  //       if (this.cardInfo.cardNumber.length % 4 == 0) {
  //           this.cardInfo.cardNumber.length += " ";
  //       }
  //   }
  // },


  
}  
}
</script>

<style scoped>
*{
  text-transform: uppercase;
}
.number-label{
  font-size: 29px;
}
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
  padding: 1rem 0 0 0;
}

.wrapper-card-text2{
  display: flex;
  justify-content: space-between;
}

.number-label{
  font-size: 29px;
}

</style>