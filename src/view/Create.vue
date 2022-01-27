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

    <label for=""  class="top-label">CARD NUMBER</label>
    <input type="number" 
    v-model="cardInfo.cardNumber"
    :numbers="numberLimit">

     <label for="">CARDHOLDER NAME</label>
    <input type="text" v-model="cardInfo.cardholder" >

    <div class="label-container">
      <label for="">MONTH</label>
      
       <label for="">YEAR</label>
    </div>

    <div class="card-container"> 
      <select class="dropdown" v-model="cardInfo.expireMonth" >

          <option 
          v-for="n in 12"
          :key="n">{{n}}</option>
        </select>    
        <select class="dropdown" v-model="cardInfo.expireYear">
          <option>22</option>
          <option>23</option>
          <option>24</option>     
          <option>25</option>
        </select>

    </div>
    <label for="">VENDOR</label>
    <div class="dropdown-container">

       <select class="dropdown" v-model="cardInfo.vendor">
          <option>Ninja Corp</option>
          <option>Evil Corp</option>
          <option>Bitcoin Empire</option>     
          <option>Chain's Gains</option>
        </select>
        <button @click="sendToAdd">ADD CARD</button>
        <!-- @click="printHome" -->
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
  vendor:"",
  cardNumber:"", 
  cardholder:"", 
  expireMonth:"", 
  expireYear:"", 
  CCV:"asdasd",
  activeCard:'false'
  },

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
  sendToAdd(){
    this.$emit('sendToAddView', "addCardView")
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
  display: flex;
  justify-content: center;
  align-items: center;
}
.top-wrap h1{
  padding: 2rem 2rem 0 2rem;
  /* margin-left: 3rem; */

  /* width: 2rem; */
  font-size: 40px;
  /* text-align: center; */
}

.top-wrap{
  widows: 100%;
  text-align: center;
}

.top-wrap p{
  margin: 1.5rem 0 1rem 0;
}



.create-container{
  width: 25.875rem;
  height: 56rem;
  background: white;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
  text-align:center ;
  /* justify-content: center;
  align-content: center; */
}

label{
  margin: 1rem 0 0 0;
}

form{
  width: 23.875rem;
  margin: 0 1rem 0 1rem;
  display: flex;
  flex-direction: column;
  /* background: yellow;   */
  text-align: start;
}

.top-label{
margin: 3rem 0 0 0;  
}

.card-container{
  display: flex;
  justify-content: space-between;
}

.label-container{
  width: 100%;
  display: flex;
}

.label-container > :first-child{
 margin-right: 25%; 
}

/* .dropdown-container{
  display: flex;
  width: 100%;
  background: pink;
  justify-content: center;
  align-items: center;
  
} */


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
/* position: absolute; */
}

/* option{
  padding-left:2rem;
} */
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