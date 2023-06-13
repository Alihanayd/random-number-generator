<template>
  <div>
    <Title />
    <Main
      :randomNumber="parseInt(randomNumber)"
      @setRandomNumber="() => setRandomNumber()"
      :min="minValue"
      :max="maxValue"
      @setMin="(value) => setMin(value)"
      @setMax="(value) => setMax(value)"
    />
    <div v-if="isError" class="alert">
      {{ errorMessage }}
    </div>
  </div>
</template>

<script>
import Title from "../components/HomeViewPartials/Title.vue";
import Main from "../components/HomeViewPartials/Main.vue";

export default {
  name: "HomeView",
  components: {
    Title,
    Main,
  },
  data() {
    return {
      randomNumber: 0,
      minValue: 0,
      maxValue: 100,
      isError: false,
      errorMessage: "",
    };
  },
  methods: {
    setRandomNumber() {
      if (this.isError) {
        return;
      }
      this.randomNumber =
        Math.floor(Math.random() * (this.maxValue - this.minValue + 1)) +
        this.minValue;
    },
    isMinValueGreaterThanMaxValue() {
      this.isError = this.minValue > this.maxValue;
      if (this.isError) {
        this.errorMessage = "Min value cannot be greater than max value";
      }
    },
    setMin(value) {
      this.minValue = value;
      this.isMinValueGreaterThanMaxValue();
    },
    setMax(value) {
      this.maxValue = value;
      this.isMinValueGreaterThanMaxValue();
    },
  },
};
</script>
<style lang="scss" scoped>
.alert {
  padding: 20px;
  background-color: #d13126;
  color: white;
  width: 30%;
  margin: 0 auto;
  text-align: center;
  font-size: 24px;
  font-weight: 700;
  border-radius: 5px;
}
</style>
