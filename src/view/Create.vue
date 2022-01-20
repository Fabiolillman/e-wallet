<template>
<div class="center-container">
  <div class="create-container">
    <h1>ADD NEW BANK CARD</h1>
    <p></p>
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
  cardNumber:"asdasdasdasdas", 
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
*{
  padding: 0;
  margin: 0;
  list-style: none;
}

.center-container{
  background: blue;
  display: flex;
  justify-content: center;
  align-items: center;
}

.create-container{
  width: 30rem;
  height: 45rem;
  background: red;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  
}

form{
  width: 80%;
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

.dropdown{
 margin-right: 40%; 
}
.dropdown-content{
 
}
</style>