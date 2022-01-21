<template>
  <div class="card">
    <h1>ADD A NEW BANK CARD</h1>
    <p>NEW CARD</p>
    <CreateCard >
     </CreateCard>
  </div>
</template>

<script>
import CreateCard from "../components/CreateCard.vue";
export default {
  components: { CreateCard },

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
