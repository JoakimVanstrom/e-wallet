<template>
  <div>
    <CreateCard :card="newCard"/>
    <form @submit.prevent="submitData">
      <article v-if="errors.length">
        <p>Please correct this errors before submit</p>
        <ul>
          <li v-for="error in errors" :key="error">{{error}}</li>
        </ul>
      </article>
      <label for="cardnumber">CARD NUMBER</label>
      <input
        type="text"
        v-model="newCard.cardNumber"
        name="cardnumber"
        id="input"
        minlength="16"
        maxlength="16"
        onkeypress="return /[0-9, Enter]/i.test(event.key)"
      />

      <label for="name">CARDHOLDER NAME</label>
      <input 
      v-model="newCard.cardName"
      type="text" 
      name="name"
      onkeypress="return /[a-ö, ' ', Enter]/i.test(event.key)"
       />

      <section class="validation">
        <div>
          <label for="month">Month</label><br />
          <select name="month" v-model="newCard.month" id="">
            <option
              v-for="month in dateMonths"
              :key="month"
              :value="month"
              selected
            >
              {{ month }}
            </option>
          </select>
        </div>
        <div>
          <label for="year">Year</label><br />
          <select name="year" v-model="newCard.year" id="">
            <option
              v-for="year in dateYears"
              :key="year"
              :value="year"
              selected
            >
              {{ year }}
            </option>
          </select>
        </div>
      </section>

      <label for="vendor">VENDOR</label>
      <select name="vendor" v-model="newCard.selectedVendor">
        <option
          v-for="option in vendors"
          :key="option.value"
          :value="option.value"
        >
          {{ option.text }}
        </option>
      </select>
      <button :class="[currentView]">Create Card</button>
    </form>
  </div>
</template>

<script>
import CreateCard from "./CreateCard.vue";
export default {
  components: { CreateCard },
  props: ["addedCards", "currentView", "errors"],
  data() {
    return {
      newCard: {
        cardNumber: "",
        cardName: "",
        month: "",
        year: "",
        selectedVendor: "previewCard",
      },
      dateMonths: {
        1: "01",
        2: "02",
        3: "03",
        4: "04",
        5: "05",
        6: "06",
        7: "07",
        8: "08",
        9: "09",
        10: "10",
        11: "11",
        12: "12",
      },
      dateYears: {
        22: "22",
        23: "23",
        24: "24",
        25: "25",
        26: "26",
        27: "27",
      },
      vendors: [
        { text: "Bitcoin inc", value: "bitcoin" },
        { text: "Evil corp", value: "evil" },
        { text: "Ninja bank", value: "ninja" },
        { text: "Block chain inc", value: "blockchain" },
      ],
    };
  },
  methods: {
    submitData() {
      this.$emit("addData", { ...this.newCard });
    },
  },
};
</script>

<style scoped lang="scss">
form {
  display: flex;
  flex-direction: column;
  padding-top: 3rem;

  input,
  select {
    height: 56px;
    border-radius: 10px;
  }
  label {
    padding-top: 1rem;
  }
}
.CreateCardPage {
  margin-top: 4rem;
  height: 72px;
  font-size: 1.5rem;
  font-weight: bolder;
  color: white;
  background-color: black;
  border-radius: 10px;
  width: 100%;
  cursor: pointer;
}
.validation {
  display: flex;
  justify-content: space-between;
  padding-top: 1rem;
  select {
    width: 175px;
  }
}
</style>
