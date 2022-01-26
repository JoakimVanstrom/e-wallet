<template>
  <section class="class-list">
      <ul>
            <CreateCard
    v-for="card in added" 
    :key="card.cardNumber"
    :card="card"
    :layerIndex="added.indexOf(card)"
    :margin="cardMargin"
    @active="$emit('active', card)"
           />
      </ul>
  </section>
</template>

<script>
import CreateCard from './CreateCard.vue'
export default {
components: {CreateCard},
props: ['added'],
data(){
  return{
    cardMargin: { marginTop: "-11rem" },
  }
}
}
</script>

<style scoped lang="scss">

</style>