<template>

          <form @submit.prevent="submitData">
      <label for="cardnumber">CARD NUMBER</label>
      <input type="text"
      v-model="eneteredCardNumber" 
      name="cardnumber" id="input"/>

      <label for="name">CARDHOLDER NAME</label>
      <input v-model="enteredName" type="text" name="name" />

    <section class="validation">
       <div>
      <label for="valid">VALID THRU</label><br>
      <input v-model="eneteredValid" type="text" name="valid" />
</div>
        <div>
      <label for="ccv">CCV</label><br>
      <input v-model="eneteredCcv" type="text" name="ccv" />
</div>
    </section>

      <label for="vendor">VENDOR</label>
      <input v-model="vendor" type="text" name="vendor" />
      <button>ADD CARD</button>
    </form>

</template>

<script>

export default {
    data(){return{
        eneteredCardNumber: "",
        enteredName: "",
        eneteredValid: "",
        eneteredCcv: "",
        vendor: "",
    }},
      computed:{
      spaceNumber(){
          let value = "";
          for(let i = 0; i < this.eneteredCardNumber.length; i++){
                if (i % 4 == 0) {
               value += " ";
        }value += this.eneteredCardNumber[i];
          }
          return value
      }
  }


}
</script>

<style scoped lang="scss">

form{
    display: flex;
    flex-direction: column;
    padding-top: 3rem;
    
input {
        height: 56px;
        border-radius: 10px;
    }
    label{
        padding-top: 1rem;
    }
}

.validation {
    display: flex;
    justify-content: space-between;
    padding-top: 1rem;
}


button {
    margin-top: 4rem;
    height: 72px;
    font-size: 1.5rem;
    font-weight: bolder;
    color: white;
    background-color: black;
    border-radius: 10px;
}

</style>