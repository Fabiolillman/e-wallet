<template>
  <div class="card-wrapper"
  :style="{ 'background-color': backgroundColor() }" >
    <div class="img-container">
    <img src="../assets/wifi.svg" alt="">
     <img v-bind:src="imageSelect" 
     
     alt="">
     <!-- :style="{ 'background-color': currentColor }" -->
     <!-- <img src="../assets/evil.svg" alt=""> -->
    <p>{{this.cardInfo.vendor}}</p>
     </div>
      <img src="../assets/chip.svg" alt="">
      <!-- <p>{{cardInfo.CCV}}</p> -->
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
      // this.backgroundColor
      // document.getElementById("myDiv").style.backgroundColor = "orange"
      return require('../assets/ninja.svg');
    } 
    // return require("../assets/" + this.cardInfo.vendor + ".svg" ) 

   return "hello"
     },

 spacedNumbers(){

   let space=''
 
   for (let i = 0; i < this.cardInfo.cardNumber.length; i++) {
    
       if (i % 4 == 0) {
            space += " ";
        } 
        // else if (space.length===16){
    
        // }
        space+=this.cardInfo.cardNumber[i]
        //  if (this.cardInfo.cardNumber.length>16) {
        //   return 
        // }
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
      return "orange"   
    } else  if (this.cardInfo.vendor==="Evil Corp") {
      return this.currentColor="red"   
    } else  if (this.cardInfo.vendor==="Bitcoin Empire") {
      return this.currentColor="purple"   
    } else  if (this.cardInfo.vendor==="Chain's Gains") {
      return this.currentColor="orange"   
    } 

     
  }
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