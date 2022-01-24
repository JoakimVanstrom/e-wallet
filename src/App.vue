<template>
  <div id="app">
  <Home 
  :home="currentView" v-if="currentView === 'home'"> </Home>
  
  <CreateCardPage
  :currentView="currentView"
  v-else-if="currentView === 'CreateCardPage'"
  :addedCards="addedCards"
  @add-card="addCard"
  @change-page="changePage"
  >
   </CreateCardPage>
  
  
  <button v-if="currentView === 'home'" :class="[currentView]" @click="changePage" >Create Card</button>
  
  </div>
</template>


<script>
import Home from './views/Home.vue'
import CreateCardPage from './views/CreateCardPage.vue'

export default {
  components:{Home, CreateCardPage},
  name: 'App',
  data(){
    return{
    currentView: 'home',
    addedCards: [],
    activeCard: {}
    };
  },
  computed:{

  },
  methods:{
    addCard(newCard){
      this.addedCards.push(newCard)
      this.currentView = 'home'
      console.log(this.addedCards)
    },

      // addCard(number, name, year, month, vendor){
      //     const newCard = {
      //         id: new Date().toISOString(),
      //         cardNumber: number,
      //         cardName: name,
      //         year: year,
      //         month: month,
      //         vendor: vendor
      //     }
      //     this.addedCards.push(newCard)
      // },
      changePage(){
        if(this.currentView === 'home'){
            this.currentView = 'CreateCardPage';
          }else{
            this.currentView = 'home';
          }
      }
  }

}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro&display=swap');

body{
  display: grid;
  place-items: center
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