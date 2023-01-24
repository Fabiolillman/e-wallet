<template>
  <div id="App">
    <nav>
      <!-- <a @click="currentView='home'">Home</a>
      <a @click="currentView='create'">Create</a> -->
  
    </nav>
  <Home v-if="currentView=='home'"
  @addCardView="changeViewToAdd"
  :itemStorage="itemStorage"/>
  <Create 
 
  v-else-if="currentView=='create'"
  @printToHome="printHomes"
   />
    <!-- printHomes(cardItems){
    // this.fullItemList=cardItems
     this.itemStorage.push(cardItem)
  } -->
  <!-- printHomes(cardItems){
    this.itemStorage.push(cardItems)
    console.log(cardItems)
  } -->
   <!-- @printToHome="printHomes" -->
  </div>
</template>

<script>
import Home from './view/HomeComponent.vue.vue'
import Create from './view/CreateComponent.vue.vue'

export default {
  name: 'App',
  components: {
  Home, 
  Create,
  },

  data(){return{
  currentView:'home',
  // cardList:[],
  fullItemList: "",
   currentItem: this.cardItems,
  itemStorage:[],

  }},

  methods:{
  changeViewToAdd(){
    this.currentView='create'
  },
 
  printHomes(cardItems){
    this.currentView='home'
    this.itemStorage.push(cardItems)
    // this.currentItem.push(cardItems)
    console.log(cardItems)
    console.log(this.itemStorage)
    
  }
  }
}
</script>

<style>

</style>
