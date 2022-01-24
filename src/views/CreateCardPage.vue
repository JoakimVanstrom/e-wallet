<template>
  <div class="card">
    <h1>ADD A NEW BANK CARD</h1>
    <p>NEW CARD</p>
<CardForm 
:currentView="currentView"
@addData="addData"
:addedCards="addedCards"> </CardForm>
 
  </div>
</template>

<script>

import CardForm from "../components/CardForm.vue"
export default {
  components: { CardForm },
  props:['addedCards', 'currentView'],
  data(){
    return {
      newData:{},

    }
  },
  methods:{
      addData(card){
      this.newData = card
      this.$emit('add-card', this.newData)
      }
    }
}


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
