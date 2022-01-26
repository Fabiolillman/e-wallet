<template>
  <div id="App">
    <nav>
      <a @click="currentView='home'">Home</a>
      <a @click="currentView='create'">Create</a>
      <!-- <p>{{cardItems.CCV}}</p> -->
    </nav>
  <Home v-if="currentView=='home'"/>
  <Create 
  v-else-if="currentView=='create'"
  @printToHome="printHomes"
   />
   <!-- @printToHome="printHomes" -->
  </div>
</template>

<script>
import Home from './view/Home.vue'
import Create from './view/Create.vue'

export default {
  name: 'App',
  components: {
  Home, 
  Create,
  },

  data(){return{
  currentView:'home',
  // cardList:[],
  fullItemList:[{

  }],

  }},

  methods:{
  
  printHomes(cardItems){
    // this.fullItemList.push(cardItems)
    console.log(cardItems)
  }
  }
}
</script>

<style>

</style>
