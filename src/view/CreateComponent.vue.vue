<template>
<div class="center-container">
  <div class="create-container">
    <div class="top-wrap">
    <h1>ADD A NEW BANK CARD</h1>
    <p>NEW CARD</p>
     
    </div>
    <CreateCard 
  :cardInfo="cardInfo"
   />
    <form action="" @submit.prevent="printHome">

    <label for="" v-if="this.errorNumber === true" class="top-label">CARD NUMBER</label>
    <label v-if="this.errorNumber === false" class="top-label error-number">MISSING CARD NUMBER</label>
    <input type="number" 
    oninput="javascript: if (this.value.length > this.maxLength) this.value = this.value.slice(0, this.maxLength);"
    v-model="cardInfo.cardNumber"
    maxlength = "16"
    :numbers="numberLimit">

     <label for="" v-if="this.errorName === true"  >CARDHOLDER NAME</label>
     <label v-if="this.errorName === false" class="error-name">MISSING CARDHOLDER NAME</label>
    <input type="text" v-model="cardInfo.cardholder"
     @keydown="checkKeyDownAlphaNumeric($event)"
     maxlength = "24"
     >

    <div class="label-container">
      <label v-if="this.errorMonth === false" class="error-name">MISSING MONTH</label>
      <label v-if="this.errorMonth === true" for="">MONTH</label>
      <label v-if="this.errorYear === false" class="error-name">MISSING YEAR</label>
       <label for="" v-if="this.errorYear === true">YEAR</label>
    </div>

    <div class="card-container"> 
      <select class="dropdown" v-model="cardInfo.expireMonth" >
 <option value="" disabled selected hidden>MM</option>
          <option 
          v-for="n in 12"
          :key="n">{{n}}</option>
        </select>    
        <select class="dropdown" v-model="cardInfo.expireYear">
          <option value="" disabled selected hidden>YY</option>

          <option>22</option>
          <option>23</option>
          <option>24</option>     
          <option>25</option>
        </select>

    </div>
    <label for="">VENDOR</label>
    <div class="dropdown-container">

       <select class="dropdown" v-model="cardInfo.vendor">
          <option value="ninja">Ninja Corp</option>
          <option value="evil">Evil Corp</option>
          <option value="bitcoin">Bitcoin Empire</option>     
          <option value="blockchain">Chain's Gains</option>
        </select>
        <button @click="sendToAdd">ADD CARD</button>
      
    </div>
    </form>
  </div>
  </div>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'
export default {
  data(){return{
  
  cardInfo:{
  vendor:"ninja",
  cardNumber:"", 
  cardholder:"", 
  expireMonth:"", 
  expireYear:"", 
  CCV:"",
  activeCard:'false'
  },
  errorNumber: true,
  errorName: true,
  errorMonth: true,
  errorYear: true,

  }},
  
components: {
  CreateCard
  },
 
 props:[
  //  'cardInfo'
 ],

 computed:{

 },
  methods:{
 checkKeyDownAlphaNumeric(event) {
      if (!/[a-zA-Z\s]/.test(event.key)) {
        this.ignoredValue = event.key ? event.key : "";
        event.preventDefault();
      }},
  
  sendToAdd(e){
      if (this.cardInfo.cardNumber!== "" && 
      this.cardInfo.cardholder!== "" && 
      this.cardInfo.expireYear.length>0&& 
      this.cardInfo.expireMonth.length>0 ) {
        this.$emit('sendToAddView', "addCardView")
      }

     if(!this.cardInfo.cardNumber ) {
     this.errorNumber=false
     e.preventDefault();
     } else{this.errorNumber=true}
      if(!this.cardInfo.cardholder){
     this.errorName=false
     e.preventDefault();
     } else{this.errorName=true}
      if(!this.cardInfo.expireMonth){
     this.errorMonth=false
     e.preventDefault();
     } else{this.errorMonth=true}
       if(!this.cardInfo.expireYear){
     this.errorYear=false
     e.preventDefault();
     } else{this.errorYear=true}
  },
   printHome(){
 
   this.$emit('printToHome', this.cardInfo)
    },
  //  addZero(){
  //    if(this.n>9){
  //      0+this.n
  //    }
  //  }
    // submit(){
    //   this.$emit('send', {...this.user})
    // }
    // this.input.value
      numberLimit(){
  // const numLimit = numbers.target.value;
   let numberCard = this.cardInfo.cardNumber
      if (numberCard.length >= 16) {
        numberCard.preventDefault();
  }
  }
    
}
}
</script>
 
<style scoped>

*{
  padding: 0;
  margin: 0;
  list-style: none;
   box-sizing: border-box;
  font-size: 18px;
}

/* #App{
  width: 100%;
    display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
} */
.center-container{
  width: 40rem;
  /* background: black; */
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}
.top-wrap h1{
  padding-top: 1rem;
   height: 98px;
  width: 250px;
  margin: auto;
  font-size: 40px;
}


.top-wrap p{
  margin: 1.5rem 0 1rem 0;
}



.create-container{
  width: 25.875rem;
  min-height: 56rem;
  background: white;
  border: 2px solid black;
  box-shadow: 0px 0px 10px 3px rgba(0,0,0,0.35) ;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  text-align:center ;

}

label{
  margin: 1rem 0 0 0;
}

form{
  width: 23.875rem;
  margin: 0 1rem 0 1rem;
  display: flex;
  flex-direction: column;
  text-align: start;
}

.top-label{
margin: 3rem 0 0 0;  
}

.error-number,.error-name{
  color: red;
}

.card-container{
  display: flex;
  justify-content: space-between;
}

.card-container select{
  width: 45%;
}

.label-container{
  width: 100%;
  display: flex;
}

.label-container > :first-child{
 margin-right: 37%; 
}

.dropdown{ 
 background: white;
 width: 100%;
 height: 3.5rem;
 border: 1px solid black;
 border-radius: 10px;
 position: relative;
}

select option{
background: rgba(111, 111, 111, 1);
/* height: 6rem; */
width: 23.8rem;
border-radius: 10px;
color: white;
padding: 0.4rem;
line-height: 2rem;
text-align: start;

}

.dropdown-content option:hover {
  width: 100%;
  /* margin: 0 1rem 0 1rem; */
  background: rgba(80, 144, 234, 1);
  border-radius: 5px;
}
input, button{
  width: 23.875rem;
  height: 3.5rem;
  border: 1px solid black;
  border-radius: 10px;
}

.card-container>Input{
width: 11rem;
}
button{
  height: 4.5rem;
  margin: 1rem 0 1rem 0;
  background: black;
  color: white;
}


</style>