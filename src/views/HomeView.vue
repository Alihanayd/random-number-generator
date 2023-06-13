<template>
  <div>
    <Title/>
    <Main
        :randomNumber="parseInt(randomNumber)"
        @setRandomNumber="() => setRandomNumber()"
        :min="minValue"
        :max="maxValue"
        @setMin="minValue = $event"
        @setMax="maxValue = $event"
    />
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
    };
  },
  methods: {
    setRandomNumber() {
      this.randomNumber = Math.floor(Math.random() * (this.maxValue - this.minValue + 1)) + this.minValue;
      console.log('Random Number: ', this.randomNumber);
      console.log('Min Value: ', this.minValue);
      console.log('Max Value: ', this.maxValue);
    },
  },
};
</script>
