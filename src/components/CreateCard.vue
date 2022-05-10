<template>
  <div class="card-wrapper"
  @click="$emit('click')"
  :class="cardInfo.vendor"
  >
    <div class="img-container">

    <img :src="wifiLogo" alt="">
     <img :src="imageSelect" 
     
     alt="">

     </div>
      <img :src="chipLogo" alt="">
      <div class="wrapper-card-text">
     
      <label for="" class="number-label">{{spacedNumbers}}</label>
      <label for="" v-if="spacedNumbers.length<1">XXXX XXXX XXXX XXXX</label>
      </div>
      <div class="wrapper-card-text2">
  
      <label for="">CARDHOLDER</label>
      <label for="">VALID THROUGH</label>
      </div>
      <div class="wrapper-card-text2">
     <!-- <label for="" v-if="spacedNumbers.length<1">XXXX </label> -->
     <label for="" v-if="this.cardInfo.cardholder.length<1">firstname   lastname</label>
     <label for="">{{cardInfo.cardholder}}</label>
     <label for="" v-if="this.cardInfo.expireMonth.length<1||this.cardInfo.cardholder.length<1">MM/YY</label>
     <label for="" v-if="this.cardInfo.expireMonth.length>0" >{{fullYear}}</label>
      
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
     
wifiLogo(){
  if(this.cardInfo.vendor=="bitcoin"){
    return require(`../assets/wifi.svg`)
  } else{
    return require(`../assets/wifi_white.svg`)
  }
},
chipLogo(){
  if(this.cardInfo.vendor=="ninja"){
    return require(`../assets/chipninja.svg`)
  } else{
    return require(`../assets/chip.svg`)
  }
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
background-color: #222222 ;
box-shadow: 0 0 8px 0px rgba(0,0,0,0.25);
color: white;
}
.evil{
background-color:#F33355 ;
box-shadow: 4px 0px 4px 0px rgba(0,0,0,0.25);
}
.bitcoin{
background-color:#FFAE34 ;
box-shadow: 0px 0px 16px 0px rgba(0,0,0,0.25);
}
.blockchain{
background-color:#8B58F9 ;
box-shadow: 4px 0px 4px 0px rgba(0,0,0,0.25);
}
.number-label{
  font-size: 29px;
}
.card-wrapper{
 border-radius: 10px;
 width: 23.875rem;
 height: 15.063rem;

 margin: 0 1rem 0 1rem;
 padding: 0 1rem 1rem 1rem;
 box-sizing: border-box;
 text-align: start ;

}

.img-container{
  display: flex;
  justify-content: space-between;
  padding: 1rem 0 0 0;
}
.wrapper-card-text{
 margin-bottom: 1.4rem;
}
.wrapper-card-text2{
  display: flex;
  justify-content: space-between;
}

.number-label{
  font-size: 29px;
}

</style>