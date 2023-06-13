<template>
  <div>
    <Header />
    <Main
      :randomNumber="parseInt(randomNumber)"
      @randomNumberMaker="() => randomNumberMaker()"
      @minValue="minValue = $event"
      @maxValue="maxValue = $event"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from "../components/HomeViewPartials/Header.vue";
import Main from "../components/HomeViewPartials/Main.vue";
export default {
  name: "HomeView",
  components: {
    Header,
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
    randomNumberMaker() {
      this.randomNumber =
        Math.floor(Math.random() * (this.maxValue - this.minValue + 1)) +
        this.minValue;
      console.log(this.randomNumber);
      console.log(this.minValue);
      console.log(this.maxValue);
    },
  },
};
</script>
