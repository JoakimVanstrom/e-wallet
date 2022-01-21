<template>
  <div id="app">
  <Home :home="currentView" v-if="currentView === 'home'"> </Home>
  
  <CreateCardPage v-else-if="currentView === 'CreateCardPage'"
    v-for="card in cards" 
    :key="card.id"
    :card="card"
    @addCard="addCard"
    >
   </CreateCardPage>
  
  
  <button :class="[currentView]" @click="changePage">Create Card</button>
  </div>
</template>


<script>
import Home from './views/Home.vue'
import CreateCardPage from './views/CreateCardPage.vue'

export default {
  components:{Home, CreateCardPage},
  name: 'App',
  data(){return{
    currentView: 'home',
    
      cards: [
        {
          id: "",
          cardNumber: "",
          cardName: "",
          valid: "",
          ccv: "",
          vendor: "",
        },
      ],
    };
  },
  methods:{
      addCard(name, num, valid, ccv, vendor){
          const newCard = {
              id: new Date().toISOString(),
              cardNumber: num,
              cardName: name,
              valid: valid,
              ccv: ccv,
              vendor: vendor
          }
          this.cards.push(newCard)
      },
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


.CreateCardPage {
    margin-top: 4rem;
    height: 72px;
    font-size: 1.5rem;
    font-weight: bolder;
    color: white;
    background-color: black;
    border-radius: 10px;
    width: 100%;
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