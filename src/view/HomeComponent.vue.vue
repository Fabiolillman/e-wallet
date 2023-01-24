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
  margin: auto;
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
.card-grid{
  margin-top: 2.5rem;
  display: grid;
  grid-auto-rows: 3rem;
  /* overflow: scroll; */
}
button{
  width: 23.875rem;
  margin: 14rem 1rem 0 1rem;
  height: 5rem;
  font-weight: 600;
  font-size: 1.3rem;
}
</style>