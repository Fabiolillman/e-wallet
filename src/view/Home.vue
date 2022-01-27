<template>
<div class="home-wrap">
  <h1>E-WALLET</h1>
  <p>Active Card</p>


<CreateCard 
v-if="activeCard"
:cardInfo="activeCard"/>


  
<div class="card-grid">


   <CreateCard
   v-for="items in itemStorage" 
   :key="items.cardNumber"
   @click="activeCard = items"
   :cardInfo="items"
               />


</div>               
  <button @click="changeView">ADD A NEW CARD</button>
</div>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'
export default {
  props:[
     "itemStorage",
  ],

  methods:{
  changeView(){
    this.$emit("addCardView", "AddNewCard")
  }
  },
   
components: {
  CreateCard
  },

  data(){return{
  activeCard:null
  }},
}
</script>

<style scoped>
.home-wrap{
   width: 25.875rem;
  height: 56rem;
  background: white;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
  text-align:center ;
}
.card-grid{
  margin-top: 2.5rem;
  display: grid;
  grid-auto-rows: 3rem;
  /* overflow: scroll; */
}
button{
  margin-top: 14rem;
  /* width: 23.875rem; */
  height: 5rem;
  font-weight: 600;
  font-size: 1.3rem;
}
</style>