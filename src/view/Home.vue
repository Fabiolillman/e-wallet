<template>
<div>
  <h1>E-WALLET</h1>
  <p>Active Card</p>


<CreateCard 
v-if="activeCard"
:cardInfo="activeCard"/>


  <p>^</p>
<div class="card-grid">


   <CreateCard
   v-for="items in itemStorage" 
   :key="items.cardNumber"
   @click="activeCard = items"
   :cardInfo="items"
               />


</div>               
  <button>ADD A NEW CARD</button>
</div>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'
export default {
  props:[
     "itemStorage",
  ],

  methods:{
  
  },
   
components: {
  CreateCard
  },

  data(){return{
  activeCard:null
  }},
}
</script>

<style>
.card-grid{
  display: grid;
  grid-auto-rows: 3rem;
  
}
</style>