<template>
<div class="center-container">
  <div class="create-container">
    <h1>ADD NEW BANK CARD</h1>
    <p>SADAS</p>
    <CreateCard 
 
  :cardInfo="cardInfo"
   />
    <form action="" @submit.prevent="">

    <label for="cardnumber">CARD NUMBER</label>
    <input type="text" for v-model="cardInfo.cardNumber">


     <label for="">CARDHOLDER NAME</label>
    <input type="text"  >

    <div class="label-container">
      <label for="">VALID THRU</label>
       <label for="">CCV</label>
    </div>

    <div class="card-container">     
    <input type="text">
    <input type="text">

    </div>
    <p>VENDOR</p>
    <div class="dropdown-container">
    <div class="dropdown">Drop down list
      <div class="dropdown-content">
        <ul>
          <li>Ninja Corp</li>
          <li>Evil Corp</li>
          <li>Bitcoin Empire</li>
           <li>{{cardInfo.CCV}}</li>
          <li>Chain's Gains</li>
        </ul>
        <button @console="console">CONSOLE</button>
        </div>
      </div>
    </div>
    </form>
  </div>
  </div>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'
export default {
components: {
  CreateCard
  },
 
 props:[
  //  'cardInfo'
 ],
  methods:{
    console(){
      // console.log(this.cardInfo)
    },
    
    // console.log(this.cardNumber)
   
    submit(){
      this.$emit('send', {...this.user})
    }
  },
    
 data(){return{
  
  cardInfo:{
  vendor:"",
  cardNumber:"", 
  cardholder:"", 
  expireMonth:"", 
  expireYear:"", 
  CCV:"asdasd",
  },

  cardList:[],

  }},
 
 
}



</script>
 
<style scoped>
/* @import url('https://fonts.googleapis.com/css2?family=Ropa+Sans&family=Source+Sans+Pro&display=swap%27);

@import url('https://fonts.googleapis.com/css2?family=Ropa+Sans&family=Source+Sans+Pro&display=swap%27);

p,button,input{
  font-family: 'Source Sans Pro', sans-serif;
}
h1{
font-family: 'Source Sans Pro', sans-serif;
font-weight: 900; */
*{
  padding: 0;
  margin: 0;
  list-style: none;
   box-sizing: border-box;
  font-size: 18px;
}

.center-container{
  width: 40rem;
  background: black;
  display: flex;
  justify-content: center;
  align-items: center;
}

.create-container{
  width: 25.875rem;
  height: 56rem;
  background: white;
  display: flex;
  flex-direction: column;
  text-align:center ;
  /* justify-content: center;
  align-content: center; */
  
}


form{
 
  width: 23.875rem;
  margin: 0 1rem 0 1rem;
  display: flex;
  flex-direction: column;
  background: yellow;  
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
 margin-right: 40%; 
}

/* .dropdown-container{
  display: flex;
  width: 100%;
  background: pink;
  justify-content: center;
  align-items: center;
  
} */

.dropdown{
  /* display: flex;
  justify-content: center; */
 /* margin-right: 40%;  */
 background: red;
 width: 100%;
 height: 3rem;

}
.dropdown-content{
background: blue;
height: 3rem;
}

input{
  width: 23.875rem;
  height: 3.5rem;
  border: 1px solid black;
  border-radius: 10px;
}

.card-container>Input{
width: 11rem;
}

</style>