<template>
  <section class="card-list">
      <ul>
            <CreateCard
    v-for="card in added" 
    :key="card.cardNumber"
    :card="card"
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
  }
}
}
</script>

<style scoped lang="scss">

.card-list {
  display: grid;
  grid-auto-rows: 2rem;
  height: 400px;

}

</style>