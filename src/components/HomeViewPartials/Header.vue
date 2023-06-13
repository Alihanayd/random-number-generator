<template>
  <div>
    <div class="text">
      <h1 class="title">Random Number Generator</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    msg: String,
    minLimit: Number,
    maxlimit: Number,
  },
};
</script>

<style lang="scss" scoped>
.title {
  font-size: 3rem;
  text-align: center;
  color: #fff;
  padding: 2rem 0;
}
</style>
