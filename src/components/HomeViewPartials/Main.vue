<template>
  <div>
    <h1 class="number">{{ randomNumber }}</h1>
    <div class="button-container">
      <button @click="setRandomNumber" class="generate-button" type="button">
        Generate Number
      </button>
    </div>
    <div class="limit-inputs-container">
      <custom-input
        :label="'Min Limit'"
        :value="min"
        @input="(value) => sendMinValue(value)"
        :placeholder="'Min Limit'"
      />

      <custom-input
        :label="'Max Limit'"
        :value="max"
        @input="(value) => sendMaxValue(value)"
        :placeholder="'Max Limit'"
      />
    </div>
  </div>
</template>

<script>
import CustomInput from "@/components/HomeViewPartials/CustomInput.vue";

export default {
  name: "Main",
  components: { CustomInput },
  props: {
    randomNumber: {
      type: Number,
      required: true,
    },
    min: {
      type: Number,
      required: true,
    },
    max: {
      type: Number,
      required: true,
    },
  },
  methods: {
    setRandomNumber() {
      this.$emit("setRandomNumber");
    },
    sendMinValue(value) {
      this.$emit("setMin", parseInt(value));
    },
    sendMaxValue(value) {
      this.$emit("setMax", parseInt(value));
    },
  },
};
</script>

<style lang="scss" scoped>
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

.limit-inputs-container {
  display: flex;
  justify-content: center;
  padding: 2rem 0;
}
</style>
