<template>
  <div class="app">
    <h1 :style="{ color }">My List</h1>
    <input type="text" v-model="currentFood" @keyup.enter="addFood" />
    <button @click="addFood">Add</button>
    <food-list :foods="foods" @stop="handleStop" />
  </div>
</template>

<script>
import FoodList from "./components/FoodList.vue";

export default {
  components: { FoodList },
  data: () => ({
    foods: ["Apple", "Cheese", "Wine", "Milk"],
    currentFood: "",
    color: "tomato"
  }),
  methods: {
    addFood() {
      this.foods.push(this.currentFood);
      this.currentFood = "";
    },
    handleStop(payload) {
      window.alert(payload);
    }
  }
};
</script>

<style>
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  display: flex;
  justify-content: center;
}

.app {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 50%;
  margin: 0 4rem;
}

input {
  height: 1.5rem;
}

button {
  background-color: rebeccapurple;
  color: aliceblue;
  outline: none;
  border: solid 1px rebeccapurple;
  height: 2rem;
  width: 100%;
  margin: 0.25rem 0;
}
</style>
