<template>
  <div id="app">
  
  
  <Home 
  :home="currentView" 
  v-if="currentView === 'home'"
  :added="addedCards"
  :active="activeCard"
  @active="activateCard"
  @delete="deleteCard"
  > </Home>
  
  <CreateCardPage
  :currentView="currentView"
  v-else-if="currentView === 'CreateCardPage'"
  :added="addedCards"
  @add-card="addCard"
  @change-page="changePage"
  >
   </CreateCardPage>
 

  <button v-if="currentView === 'home'"  :class="[currentView]" @click="changePage" >Create Card</button>

  </div>
</template>


<script>
import Home from './views/Home.vue'
import CreateCardPage from './views/CreateCardPage.vue'

function persist(data){
  localStorage.setItem('cardData', JSON.stringify(data))
}

export default {
  components:{Home, CreateCardPage},
  name: 'App',
  data(){
    return{
    currentView: 'home',
    addedCards: [],
    activeCard: {selectedVendor: "previewCard"}
    };
  },
  created(){
    let persistData = localStorage.getItem('cardData')
    if (persistData){
      this.addedCards = JSON.parse(persistData)
    }
  },
  methods:{
    addCard(card){
      this.addedCards.push(card)
      this.currentView = 'home'
      persist(this.addedCards)
    },

      changePage(){
        if(this.currentView === 'home'){
            this.currentView = 'CreateCardPage';
          }else{
            this.currentView = 'home';
          }
      },
      activateCard(card) {
      this.activeCard = card
  },
  deleteCard(){
    this.addedCards = this.addedCards.filter(
      (card) => card.cardNumber != this.activeCard.cardNumber
    )
  persist(this.addedCards)
  localStorage.removeItem(this.activeCard)
  this.activeCard = {}
  }
}
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro&display=swap');

#app{
  display: grid;
  place-items: center;
}


.home {
    margin-top: 4rem;
    height: 72px;
    font-size: 1.5rem;
    font-weight: bolder;
    color: black;
    background-color: white;
    border-radius: 10px;
}

// font-family: 'PT Mono', monospace;
// font-family: 'Source Sans Pro', sans-serif;
</style>