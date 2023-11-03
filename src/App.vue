<script>
export default {
  data: () => {
    return {
      EUR: {
        toUSD: 1.06,
        toRUB: 99.66,
        toEUR: 1,
      },
      USD: {
        toUSD: 1,
        toEUR: 0.95,
        toRUB: 94.2,
      },
      RUB: {
        toRUB: 1,
        toEUR: 0.01,
        toUSD: 0.011,
      },
      value: "",
      convertedValue: "",
      selectOne: "",
      selectTwo: "",
    };
  },
  watch: {
    selectOne() {
      localStorage.info = JSON.stringify({
        inputValue: this.value,
        outputValue: this.convertedValue,
        selectOne: this.selectOne,
        selectTwo: this.selectTwo,
      });
      if (this.selectOne && this.selectTwo) {
        this.convertedValue =
          this[this.selectOne][`to${this.selectTwo}`] * this.value;
      } else {
        this.convertedValue = "";
      }
    },
    selectTwo() {
      localStorage.info = JSON.stringify({
        inputValue: this.value,
        outputValue: this.convertedValue,
        selectOne: this.selectOne,
        selectTwo: this.selectTwo,
      });
      if (this.selectOne && this.selectTwo) {
        this.convertedValue =
          this[this.selectOne][`to${this.selectTwo}`] * this.value;
      } else {
        this.convertedValue = "";
      }
    },
    value() {
      localStorage.info = JSON.stringify({
        inputValue: this.value,
        outputValue: this.convertedValue,
        selectOne: this.selectOne,
        selectTwo: this.selectTwo,
      });
      if (this.selectOne && this.selectTwo) {
        this.convertedValue =
          this[this.selectOne][`to${this.selectTwo}`] * this.value;
      } else {
        this.convertedValue = "";
      }
    },
  },
  mounted() {
    if (localStorage.info) {
      const info = JSON.parse(localStorage.info);
      this.selectOne = info.selectOne;
      this.selectTwo = info.selectTwo;
      this.value = info.inputValue;
      this.convertedValue = info.outputValue;
    } else {
      this.selectOne = "EUR";
      this.selectTwo = "EUR";
      this.value = 1;
      this.convertedValue = "";
    }
  },
};
</script>

<template>
  <div class="centered">
    <input type="number" min="1" v-model="value" />
    <p class="text">From</p>
    <select v-model="selectOne">
      <option value="EUR">EUR</option>
      <option value="RUB">RUB</option>
      <option value="USD">USD</option>
    </select>
    <p class="text">To</p>
    <select v-model="selectTwo">
      <option value="EUR">EUR</option>
      <option value="RUB">RUB</option>
      <option value="USD">USD</option>
    </select>
    <input type="number" readonly v-model="convertedValue" />
  </div>
</template>

<style scoped>
.centered {
  width: 600px;
  margin: 0 auto;
  display: flex;
  justify-content: space-evenly;
  padding: 15px 0 0 0;
}
.text {
  color: black;
}
</style>
