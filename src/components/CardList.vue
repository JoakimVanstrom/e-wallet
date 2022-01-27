<template>
  <section class="class-list">
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

</style>