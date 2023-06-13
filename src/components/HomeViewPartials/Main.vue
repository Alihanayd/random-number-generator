<template>
  <div>
    <h1 class="number">{{ randomNumber }}</h1>
    <div class="button-container">
      <button @click="randomNumberMaker" class="generate-button" type="button">
        Generate Number
      </button>
    </div>
    <div class="limitInp">
      <input
        :value="minValue"
        @input="sendMinValue($event.target.value)"
        type="number"
        placeholder="Min Limit"
      />
      <input
        :value="maxValue"
        @input="sendMaxValue($event.target.value)"
        type="number"
        placeholder="Max Limit"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "Main",
  props: {
    msg: String,
    randomNumber: Number,
    minValue: Number,
    maxValue: Number,
  },
  methods: {
    randomNumberMaker() {
      this.$emit("randomNumberMaker");
    },
    sendMinValue(value) {
      console.log(value, typeof value);
      this.$emit("minValue", parseInt(value));
    },
    sendMaxValue(value) {
      this.$emit("maxValue", parseInt(value));
    },
  },
};
</script>

<style lang="scss" scoped>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
.generate-button {
  background-color: #6cd4ff;
  border: none;
  border-radius: 5px;
  color: #2c363f;
  padding: 15px 32px;
  text-align: center;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}
.button-container {
  display: flex;
  justify-content: center;
}
.number {
  font-size: 3rem;
  text-align: center;
  margin: 2rem 0;
  color: #fff;
}
.limitInp {
  display: flex;
  justify-content: center;
  padding: 2rem 0;
}
.limitInp input {
  width: 100px;
  height: 30px;
  margin: 0 10px;
  border-radius: 5px;
  border: none;
  text-align: center;
  font-size: 16px;
  color: #2c363f;
}
</style>
