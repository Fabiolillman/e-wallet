<template>
  <div id="App">
    <nav>
      <a @click="currentView='home'">Home</a>
      <a @click="currentView='create'">Create</a>
    </nav>
  <Home v-if="currentView=='home'"/>
  <Create 
  v-else-if="currentView=='create'"
   />
  </div>
</template>

<script>
import Home from './view/Home.vue'
import Create from './view/Create.vue'

export default {
  name: 'App',
  components: {
  Home,Create
  },

  data(){return{
  currentView:'home',
  cardList:[],

  }},

  methods:{
  
  }
}
</script>

<style>

</style>
