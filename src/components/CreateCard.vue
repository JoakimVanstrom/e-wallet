<template>
  <div class="create-card">
    <article class="preview-card" :class="[card.selectedVendor]">
      <header>
        <div class="card-icons">
          <img
            v-if="card.selectedVendor === 'ninja'"
            src="../assets/wifi_white.svg"
            alt=""
          />
          <img v-else id="wifi" src="../assets/wifi.svg" alt="" />
          <img id="chip" src="../assets/chip.svg" alt="" />
        </div>
        <div class="vendoricon">
          <img :src="iconPath" alt="" />
        </div>
      </header>
      <p class="credNumbers" v-if="card.cardNumber">{{ spaceNumber }}</p>
      <p class="credNumbers" v-else>
        XXXX XXXX XXXX XXXX
      </p>
      <div class="names">
        <p>CARDHOLDER NAME</p>
        <p>VALID THRU</p>
      </div>
      <div class="enteredValue">
        <span>{{ card.cardName }}</span>
        <span>{{ card.month }}/{{ card.year }}</span>
      </div>
    </article>
  </div>
</template>

<script>
export default {
 props: ['card'],
  data() {
    return {

        };
  },
  computed: {
    spaceNumber() {
      let value = "";
      for (let i = 0; i < this.card.cardNumber.length; i++) {
        if (i % 4 == 0) {
          value += " ";
        }
        value += this.card.cardNumber[i];
      }
      return value;
    },
    iconPath(){
      return require(`../assets/${this.card.selectedVendor}.svg`)
    }
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

.evil {
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

.bitcoin {
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
.ninja {
  color: white;
  background: linear-gradient(
      248.3deg,
      rgba(255, 255, 255, 0.15) 0%,
      rgba(255, 255, 255, 0) 100%
    ),
    #222222;
  #wifi {
    color: white;
  }
  #chip {
    background: white;
    border-radius: 10px;
  }
}
.blockchain {
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
</style>
