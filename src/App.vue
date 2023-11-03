<script>
export default {
  data: () => {
    return {
      inputValue: "",
    };
  },
  methods: {
    addNum(event) {
      this.inputValue += event.target.value;
    },
    setRes() {
      this.inputValue = eval(this.inputValue);
    },
  },
};
</script>

<template>
  <div class="center">
    <div class="calc">
      <input class="input" readonly type="text" v-model="inputValue" />
      <div class="buttons">
        <div class="block-one">
          <input
            type="button"
            value="<"
            class="border-one"
            @click="inputValue = inputValue.toString().slice(0, -1)"
          />
          <input type="button" value="%" class="border-one" @click="addNum" />
          <input
            type="button"
            value="Sqrt"
            class="border-one"
            @click="inputValue = Math.sqrt(inputValue)"
          />
          <input
            type="button"
            value="C"
            class="border-one"
            @click="inputValue = ''"
          />
        </div>
        <div class="block-one">
          <input type="button" value="7" class="border-two" @click="addNum" />
          <input type="button" value="8" class="border-two" @click="addNum" />
          <input type="button" value="9" class="border-two" @click="addNum" />
          <input type="button" value="+" class="border-one" @click="addNum" />
          <input type="button" value="-" class="border-one" @click="addNum" />
        </div>
        <div class="block-one">
          <input type="button" value="4" class="border-two" @click="addNum" />
          <input type="button" value="5" class="border-two" @click="addNum" />
          <input type="button" value="6" class="border-two" @click="addNum" />
          <input type="button" value="*" class="border-one" @click="addNum" />
          <input type="button" value="/" class="border-one" @click="addNum" />
        </div>
        <div class="block-two">
          <div class="block-inner">
            <div class="block-one">
              <input
                type="button"
                value="1"
                class="border-two"
                @click="addNum"
              />
              <input
                type="button"
                value="2"
                class="border-two"
                @click="addNum"
              />
              <input
                type="button"
                value="3"
                class="border-two"
                @click="addNum"
              />
            </div>
            <div class="block-one">
              <input
                type="button"
                value="0"
                class="border-two big-two"
                @click="addNum"
              />
              <input
                type="button"
                value="."
                class="border-two big-two"
                @click="addNum"
              />
            </div>
          </div>
          <input
            type="button"
            value="="
            class="border-one big-one"
            @click="setRes"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
.center {
  width: 500px;
  margin: 0 auto;
  padding: 15px 0 0 0;
  display: flex;
  justify-content: center;
}
.calc {
  width: 210px;
  height: 280px;
  border: 2px solid teal;
  border-radius: 15px;
  background: white;
  padding: 13px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.input {
  width: 100%;
  padding: 10px 5px;
  outline: none;
  border-radius: 5px;
  border: 2px solid teal;
  text-align: right;
  font-weight: 600;
}
.buttons {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 7px;
}
.block-one {
  display: flex;
  justify-content: space-between;
  height: 30px;
}
.block-two {
  display: flex;
  justify-content: space-between;
  height: 70px;
}
.border-one {
  border: 2px solid teal;
  border-radius: 3px;
  cursor: pointer;
}
.border-two {
  border: 2px solid gray;
  border-radius: 3px;
  cursor: pointer;
}
.big-one {
  width: 70px;
}
.big-two {
  width: 45px;
}
.block-inner {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 100px;
}
</style>
