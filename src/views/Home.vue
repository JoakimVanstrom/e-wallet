<template>
  <div class="home">
      <h1>E-Wallet</h1>
     <p>Active card</p>
     <!-- <CreateCard 
    :active="activeCard"
     ></CreateCard> -->

     <CardList
     :added="added"
     @active="submitCard"
     ></CardList>
  </div>
</template>

<script>
// import CreateCard from '../components/CreateCard.vue'
import CardList from '../components/CardList.vue'
export default {
components: { CardList},
props: ['added', 'active'],
data(){return{
  activeCardData: {}
}},
methods:{
  submitCard(card){
    this.activeCardData = card;
    this.$emit('active', this.activeCardData)
  }
}
}
</script>

<style scoped lang="scss">
.home{
  display: flex;
  flex-direction: column;
}

</style>