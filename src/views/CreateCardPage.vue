<template>
  <div class="card">
    <h1>ADD A NEW BANK CARD</h1>
    <p>NEW CARD</p>
    <CreateCard 
    v-for="card in cards" 
    :key="card.id"
    :id="card.id"
    :cardNumber="card.cardNumber"
    :cardName="card.cardName"
    :valid="card.valid"
    :ccv="card.ccv"> </CreateCard>
  </div>
</template>

<script>
import CreateCard from "../components/CreateCard.vue";
export default {
  components: { CreateCard },
  data() {
    return {
      cards: [
        {
          id: "3",
          cardNumber: "1234 5678 1234 5678",
          cardName: "Joakim Vanström",
          valid: "12/12",
          ccv: "339",
          vendor: "hej",
        },
      ],
    };
  },
  methods:{
      addCard(name, num, valid, ccv){
          const newCard = {
              id: new Date().toISOString(),
              cardNumber: num,
              cardName: name,
              valid: valid,
              ccv: ccv
          }
          this.cards.push(newCard)
      }
  }
};
</script>

<style scoped lang="scss">
h1 {
    font-family: 'Source Sans Pro', sans-serif;
    text-align: center;
}
p{
    text-align: center;
}
</style>
