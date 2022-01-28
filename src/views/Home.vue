<template>
  <div class="home-wrapper">
      <h1>E-Wallet</h1>
      <p>Active card</p>
     <CreateCard 
    :card="getCard"
     @delete="$emit('delete', activeCard)"
     ></CreateCard>
 
     <CardList
     :added="added"
     @active="activateCard"
    class="cardlist"
     ></CardList>

         <button
      v-if="currentView === 'home'"
      :class="[currentView]"
      @click="$emit('changePage')"
    >
      Create Card
    </button>
 
  </div>
</template>

<script>
import CreateCard from '../components/CreateCard.vue'
import CardList from '../components/CardList.vue'

export default {
components: { CardList, CreateCard},
props: ['added', 'active', 'currentView'],
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

.home-wrapper{
display: grid;

}
h1{
  font-family: 'Source Sans Pro', sans-serif;
  font-size: 3rem;
  text-align: center;
  }
p{
  font-family: 'PT Mono', monospace;
  text-align: center;
}
.cardlist {
  padding-top: 3rem;
}

.home {
  margin-top: 15rem;
  font-size: 1.5rem;
  font-weight: bolder;
  color: black;
  background-color: white;
  border-radius: 10px;
  height: 72px;
}

</style>