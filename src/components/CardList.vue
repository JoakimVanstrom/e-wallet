<template>
  <div>
      <ul>
            <CreateCard
    v-for="card in added" 
    :key="card.cardNumber"
    :card="card"
    @active="$emit('active', card)"
           />
      </ul>
  </div>
</template>

<script>
import CreateCard from './CreateCard.vue'
export default {
components: {CreateCard},
props: ['added']
}
</script>

<style scoped lang="scss">

</style>