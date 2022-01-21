<template>
  <div class="create-card">
    <article class="preview-card" :class="[selectedVendor]">
      <header>
        <div class="card-icons">
          <img src="../assets/wifi.svg" alt="" />
          <img id="chip" src="../assets/chip.svg" alt="" />
        </div>
        <div class="vendoricon">
          <img v-if="selectedVendor === 'EC'" :src="EC" alt="" />
          <img v-else-if="selectedVendor === 'BI'" :src="BI" alt="" />
          <img v-else-if="selectedVendor === 'NB'" :src="NB" alt="" />
          <img v-else-if="selectedVendor === 'BCI'" :src="BCI" alt="" />
        </div>
      </header>
      <p class="credNumbers" v-if="eneteredCardNumber.length <= 0">
        XXXX XXXX XXXX XXXX
      </p>
      <p class="credNumbers" v-else>{{ spaceNumber }}</p>
      <div class="names">
        <p>CARDHOLDER NAME</p>
        <p>VALID THRU</p>
      </div>
      <div class="enteredValue">
        <span>{{ enteredName }}</span>
        <span>12/12</span>
      </div>
    </article>
    <div>
      <form @submit.prevent="submitData">
        <label for="cardnumber">CARD NUMBER</label>
        <input
          type="text"
          v-model="eneteredCardNumber"
          name="cardnumber"
          id="input"
        />

        <label for="name">CARDHOLDER NAME</label>
        <input v-model="enteredName" type="text" name="name" />

        <section class="validation">
          <div>
            <label for="valid">VALID THRU</label><br />
            <input v-model="eneteredValid" type="text" name="valid" />
          </div>
          <div>
            <label for="ccv">CCV</label><br />
            <input v-model="eneteredCcv" type="text" name="ccv" />
          </div>
        </section>

        <label for="vendor">VENDOR</label>
        <select name="vendor" v-model="selectedVendor">
          <option
            v-for="option in vendors"
            :key="option.value"
            :value="option.value"
          >
            {{ option.text }}
          </option>
        </select>

        <button>ADD CARD</button>
      </form>
    </div>
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
      selectedVendor: "previewCard",
      vendors: [
        { text: "Bitcoin inc", value: "BI" },
        { text: "Evil corp", value: "EC" },
        { text: "Ninja bank", value: "NB" },
        { text: "Block chain inc", value: "BCI" },
      ],
      EC: require("../assets/evil.svg"),
      BI: require("../assets/bitcoin.svg"),
      NB: require("../assets/ninja.svg"),
      BCI: require("../assets/blockchain.svg"),
    };
  },
  computed: {
    spaceNumber() {
      let value = "";
      for (let i = 0; i < this.eneteredCardNumber.length; i++) {
        if (i % 4 == 0) {
          value += " ";
        }
        value += this.eneteredCardNumber[i];
      }
      return value;
    },
  },
};
</script>

<style scoped lang="scss">
.create-card {
  width: 382px;
}

.preview-card {
  height: 241px;
  font-family: "PT Mono", monospace;
  margin: 0;
  border-radius: 10px;
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.08);
}
header {
  display: flex;
  justify-content: space-between;
}

.vendoricon {
  display: flex;
  justify-content: flex-end;
  padding: 2rem 2rem 0 0;
  img {
    width: 70px;
  }
}

.card-icons {
  display: flex;
  flex-direction: column;
  width: 50px;
  padding: 2rem 0 0 1rem;
}
.credNumbers {
  margin: 1rem 0.7rem 0 0.7rem;
  font-size: 29px;
}

.EC {
  color: white;
  background: linear-gradient(
      248.3deg,
      rgba(0, 0, 0, 0.16) 0%,
      rgba(0, 0, 0, 0) 100%
    ),
    #f33355;
  #chip {
    background: lightgrey;
    border-radius: 10px;
  }
}

.BI {
  background: linear-gradient(
      248.04deg,
      rgba(255, 255, 255, 0.15) 0%,
      rgba(255, 255, 255, 0) 99.07%
    ),
    #ffae34;
      #chip {
    background: white;
    border-radius: 10px;
  }
}
.NB {
  background: linear-gradient(
      248.3deg,
      rgba(255, 255, 255, 0.15) 0%,
      rgba(255, 255, 255, 0) 100%
    ),
    #222222;
}
.BCI {
  background: linear-gradient(
      248.52deg,
      rgba(0, 0, 0, 0.15) 1.49%,
      rgba(0, 0, 0, 0) 100%
    ),
    #8b58f9;
}

.previewCard {
  background: linear-gradient(
      248.3deg,
      rgba(255, 255, 255, 0.24) 0%,
      rgba(255, 255, 255, 0) 100%
    ),
    #d0d0d0;
}

.names {
  padding: 1.5rem 0.7rem 0 0.7rem;
  display: flex;
  justify-content: space-between;
  font-size: 0.8rem;
  p {
    margin: 0;
  }
}
.enteredValue {
  padding: 0.4rem 0.7rem 0 0.7rem;
  display: flex;
  justify-content: space-between;
  font-weight: bold;
}
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
