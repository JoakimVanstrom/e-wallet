<template>
  <div class="home">
      <h1>E-Wallet</h1>
     <p>Active card</p>
     <CreateCard 
      :cardNumber="activeCard.cardNumber"
      :cardName="activeCard.cardName"
      :month="activeCard.month"
      :year="activeCard.year"
      :selectedVendor="activeCard.selectedVendor"
     ></CreateCard>

     <CardList
     :cards="cards"
     @activeCard="submitCard"
     ></CardList>
  </div>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'
import CardList from '../components/CardList.vue'
export default {
components: {CreateCard, CardList},
props: ['cards', 'activeCard'],
data(){return{
  activeCardData: {}
}},
methods:{
  submitCard(card){
    this.activeCardData = card;
    this.$emit('activeCard', this.activeCardData)
  }
}
}
</script>

<style scoped lang="scss">

</style>