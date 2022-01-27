<template>
  <div class="home">
      <h1>E-Wallet</h1>
     <p>Active card</p>
     <CreateCard 
    :card="getCard"
     @delete="$emit('delete', activeCard)"
     ></CreateCard>

     <CardList
     :added="added"
     @active="activateCard"
    
     ></CardList>
  </div>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'
import CardList from '../components/CardList.vue'

export default {
components: { CardList, CreateCard},
props: ['added', 'active'],
  data(){return{
          activeCardData: {},
          activeCard: this.added[0].cardNumber
         

  }},
methods: {
    activateCard(card) {
      this.activeCard = card.cardNumber;
    },
},
computed: {
  getCard(){
    for(let i = 0; i < this.added.length; i++){
      if(this.added[i].cardNumber === this.activeCard){
      return this.added[i]
    }
    }
    return this.added[0]
    }
}
}
</script>

<style scoped lang="scss">

.home{
  display: flex;
  flex-direction: column;
}
  h1{
  font-family: 'Source Sans Pro', sans-serif;
  }
p{
  font-family: 'PT Mono', monospace;

}

</style>