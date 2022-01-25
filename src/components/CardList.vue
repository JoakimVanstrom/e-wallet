<template>
  <div>
      <ul>
            <CreateCard
    v-for="card in cards" 
    :key="card.cardNumber"
    :cardNumber="card.cardNumber"
    :cardName="card.cardName"
    :month="card.month"
    :year="card.year"
    :selectedVendor="card.selectedVendor"
    @submitCard="$emit('submitCard', card)"
            ></CreateCard>
      </ul>
  </div>
</template>

<script>
import CreateCard from './CreateCard.vue'
export default {
components: {CreateCard},
props: ['cards', 'submitCard']
}
</script>

<style>

</style>