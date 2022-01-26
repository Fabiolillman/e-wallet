<template>
<div>
  <h1>E-WALLET</h1>
  <p>Active Card</p>
   <CreateCard 
  :cardInfo="cardInfo"
   />
  <button>ADD A NEW CARD</button>
</div>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'
export default {
components: {
  CreateCard
  },
}
</script>

<style>

</style>