<template>
  <div class="create-card">
    <article class="preview-card">
      <div class="card-icons">
        <img src="../assets/wifi.svg" alt="" />
        <img src="../assets/chip.svg" alt="" />
      </div>
      <p id="number">1234 5678 1234 5678</p>
      <div class="names">
        <p>CARDHOLDER NAME</p>
         <p>VALID THRU</p>
      </div>
      <div class="enteredValue">
       <span>Joakim Vanström</span>
       <span>12/12</span>
      </div>
    </article>

    <form @submit.prevent="submitData">
      <label for="cardnumber">CARD NUMBER</label>
      <input v-model="eneteredCardNumber" type="text" name="cardnumber" id="" />

      <label for="name">CARDHOLDER NAME</label>
      <input v-model="enteredName" type="text" name="name" />
    <div class="validation">
      <label for="valid">VALID THRU</label>
      <input v-model="eneteredValid" type="text" name="valid" />

      <label for="cvv">CCV</label>
      <input v-model="eneteredCcv" type="text" name="cvv" />
</div>
      <label for="vendor">VENDOR</label>
      <input v-model="vendor" type="text" name="vendor" />
      <button>ADD CARD</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      eneteredCardNumber: "",
      enteredName: "",
      eneteredValid: "",
      eneteredCcv: "",
      vendor: "",
    };
  },
};
</script>

<style scoped lang="scss">

.preview-card {
    width: 382px;
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
#number {
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
form {
          display: flex;
          flex-direction: column;
        }
input {
        height: 56px;
        border-radius: 10px;
    }
.validation{
    input{
        width: 40%;
    }
}
</style>
