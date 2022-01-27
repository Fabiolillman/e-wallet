<template>
  <div class="card-wrapper"
  @click="$emit('click')"
  :class="cardInfo.vendor"
  >
    <div class="img-container">

    <img src="../assets/wifi.svg" alt="">
     <img :src="imageSelect" 
     
     alt="">

     </div>
      <img src="../assets/chip.svg" alt="">
      <div class="wrapper-card-text">
     
      <label for="" class="number-label">{{spacedNumbers}}</label>
      <label for="" v-if="spacedNumbers.length<1">XXXX XXXX XXXX XXXX</label>
      </div>
      <div class="wrapper-card-text2">
  
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
    return require(`../assets/${this.cardInfo.vendor}.svg` ) 
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

}  
}
</script>

<style scoped>
*{
  text-transform: uppercase;
}

.ninja{
background-color: rgba(0,0,0,0.5) ;
}
.evil{
background-color:#F33355 ;
}
.bitcoin{
background-color:#FFAE34 ;
}
.blockchain{
background-color:#8B58F9 ;
}
.number-label{
  font-size: 29px;
}
.card-wrapper{
 border-radius: 10px;
 width: 23.875rem;
 height: 15.063rem;

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