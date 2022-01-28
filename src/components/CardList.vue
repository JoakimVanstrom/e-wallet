<template>
<div>
  <section class="card-list">
      
            <CreateCard
    v-for="card in added" 
    :key="card.cardNumber"
    :card="card"
    @active="$emit('active', card)"
           />
    
  </section>
  </div>
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
  grid-auto-rows: 3.5rem;
}

</style>