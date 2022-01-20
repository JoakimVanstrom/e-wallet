<template>
  <div class="create-card">
    <article class="preview-card">
      <div class="card-icons">
        <img src="../assets/wifi.svg" alt="" />
        <img src="../assets/chip.svg" alt="" />
      </div>
      <p class="credNumbers">XXXX XXXX XXXX XXXX</p>
      <p class="credNumbers" ></p>
      <div class="names">
        <p>CARDHOLDER NAME</p>
         <p>VALID THRU</p>
      </div>
      <div class="enteredValue">
       <span>Joakim Vanström</span>
       <span>12/12</span>
      </div>
    </article>
    <CreateCardForm></CreateCardForm>
  </div>
</template>

<script>
import CreateCardForm from './CreateCardForm.vue'
export default {
    components: { CreateCardForm
    },
  data() {
    return {
    };
  },


};
</script>

<style scoped lang="scss">
.create-card{
    width: 382px;
}

.preview-card {
  height: 241px;
  background-color: #d0d0d0;
  font-family: 'PT Mono', monospace;
  margin: 0;
  border-radius: 10px;
}
.card-icons{
    display: flex;
    flex-direction: column;
    width: 50px;
    padding-left: 1rem;
    padding-top: 1.5rem;
}
.credNumbers {
    margin: 1rem 0.7rem 0 0.7rem;
    font-size: 29px;
}
.names {
    padding: 1.5rem 0.7rem 0 0.7rem;
    display: flex;
    justify-content: space-between;
    font-size: 0.8rem;
    p{
        margin: 0;
    }
}
.enteredValue{
    padding: 0.4rem 0.7rem 0 0.7rem;
    display: flex;
    justify-content: space-between;
    font-weight: bold;
   
}



</style>
