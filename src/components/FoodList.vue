<template>
  <ul>
    <li v-for="food in foods" :key="food">{{ food }}</li>
  </ul>
</template>

<script>
const MAX_FOODS = 5;

export default {
  props: {
    foods: { type: Array, default: () => [] }
  },
  watch: {
    foods() {
      if (this.foods.length >= MAX_FOODS) {
        this.$emit("stop", "Tá cheio");
      }
    }
  }
};
</script>

<style scoped>
ul {
  margin: 1rem 0;
  padding: 0;
  list-style-type: none;
}

li {
  padding: 0.25rem;
  border: salmon 1px solid;
  margin: 0.5rem 0;
}
</style>
