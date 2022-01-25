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
  </div>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'
export default {
components: {CreateCard},
props: ['cards', 'activeCard'],
data(){return{
  activeCardData: {}
}},
methods:{
  submitCard(e){
    this.activeCardData = e;
    this.$emit('activeCard', this.activeCardData)
  }
}
}
</script>

<style scoped lang="scss">

</style>