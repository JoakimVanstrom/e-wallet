<template>
  <div id="app">
    <Home
      :currentView="currentView"
      v-if="currentView === 'home'"
      :added="addedCards"
      @delete="deleteCard"
      @changePage="changePage"
    
    />

    <CreateCardPage
      :currentView="currentView"
      v-else-if="currentView === 'CreateCardPage'"
      :added="addedCards"
      @add-card="addCard"
      @change-page="changePage"
    :errors="errors"
    />
  </div>
</template>

<script>
import Home from "./views/Home.vue";
import CreateCardPage from "./views/CreateCardPage.vue";

function persist(data) {
  localStorage.setItem("cardData", JSON.stringify(data));
}

export default {
  components: { Home, CreateCardPage },
  name: "App",
  data() {
    return {
      currentView: "home",
      addedCards: [],
      errors: []
    };
  },
  created() {
    let persistData = localStorage.getItem("cardData");
    if (persistData) {
      this.addedCards = JSON.parse(persistData);
    }
  },
  methods: {
    addCard(card) {
      this.errors = []
      for (let i = 0; i < this.addedCards.length; i++) {
        if (this.addedCards[i].cardNumber === card.cardNumber) {
          return this.errors.push('Cardnumber already exist');
        }
      }if(card.cardNumber === ''){
        return this.errors.push('Cardnumber required')
      }if(card.cardName === ''){
        return this.errors.push('Name required')
      }if(card.month === ''){
        return this.errors.push('Month required')
      } if(card.year === ''){
        return this.errors.push('Year required')
      } if(card.vendor === ''){
        return this.errors.push('Vendor required')
      }

      this.addedCards.push(card);
      this.currentView = "home";
      persist(this.addedCards);
    },
    changePage() {
      if (this.currentView === "home") {
        this.currentView = "CreateCardPage";
      } else {
        this.currentView = "home";
      }
    },
    deleteCard(cardNumber) {
      this.addedCards = this.addedCards.filter(
        (card) => card.cardNumber != cardNumber
      );
      persist(this.addedCards);
      localStorage.removeItem(this.activeCard);
      this.activeCard = this.addedCards[0];
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&family=Source+Sans+Pro&display=swap");

#app {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
  background-color: white;
}

// font-family: 'PT Mono', monospace;
// font-family: 'Source Sans Pro', sans-serif;
</style>
