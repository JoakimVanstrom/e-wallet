<template>
  <div class="home-wrapper">
    <Dialog 
    v-if="showDialog"
    @close="showDialog = false"
    @delete="$emit('delete', activeCard)"
     />
    <h1>E-Wallet</h1>
    <p>Active card</p>
    <CreateCard
      :card="getCard"
    />

    <CardList :added="added" @active="activateCard" class="cardlist"/>

    <button
      v-if="currentView === 'home'"
      :class="[currentView]"
      @click="$emit('changePage')"
    >
      Create Card
    </button>
    <button 
    class="delete-btn"
    @click="showDialog = true"
    >Delete Card</button>
  </div>
</template>

<script>
import CreateCard from "../components/CreateCard.vue";
import CardList from "../components/CardList.vue";
import Dialog from "../components/Dialog.vue"
export default {
  components: { CardList, CreateCard, Dialog },
  props: ["added", "active", "currentView"],
  data() {
    return {
      activeCardData: {},
      activeCard: this.added[0].cardNumber,
      showDialog: false
    };
  },
  methods: {
    activateCard(card) {
      this.activeCard = card.cardNumber;
    },
  },
  computed: {
    getCard() {
      for (let i = 0; i < this.added.length; i++) {
        if (this.added[i].cardNumber === this.activeCard) {
          return this.added[i];
        }
      }
      return this.added[0];
    },
  },
};
</script>

<style scoped lang="scss">
.home-wrapper {
  display: grid;
}

h1 {
  font-family: "Source Sans Pro", sans-serif;
  font-size: 3rem;
  text-align: center;
}
p {
  font-family: "PT Mono", monospace;
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
  cursor: pointer;
}
.delete-btn{
  margin-top: 2rem;
  font-size: 1.5rem;
  font-weight: bolder;
  color: black;
  background-image: linear-gradient(to left, red,orange,yellow,green,blue,indigo,violet);
  border-radius: 10px;
  height: 72px;
  cursor: pointer;
}
</style>
