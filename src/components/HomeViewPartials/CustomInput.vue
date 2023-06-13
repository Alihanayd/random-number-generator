<template>
  <div class="input-container">
    <label for="input">{{ label }}</label>
    <input
      id="input"
      :value="value"
      @input="sendEmit($event.target.value)"
      type="number"
      :placeholder="placeholder"
    />
  </div>
</template>

<script>
export default {
  name: "CustomInput",
  props: {
    label: {
      type: String,
      default: "",
    },
    value: {
      type: Number,
      required: true,
    },
    placeholder: {
      type: String,
      default: "",
    },
  },
  methods: {
    sendEmit(value) {
      this.$emit("input", parseInt(value));
    },
  },
};
</script>

<style scoped lang="scss">
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

.input-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
}

.input-container label {
  color: #fff;
  margin-bottom: 12px;
}

.input-container input {
  width: 120px;
  height: 50px;
  margin: 0 10px;
  border-radius: 5px;
  border: none;
  text-align: center;
  font-size: 24px;
  color: #2c363f;
}
</style>
