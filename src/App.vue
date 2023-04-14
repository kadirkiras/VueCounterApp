<template>
  <main>
    <div>
      <h4>The current count is...</h4>
      <h1>{{ boundedCount }}</h1>
      <button @click="decrementCount">-</button>
      <button @click="incrementCount">+</button>
    </div>
  </main>
</template>

<style scoped>
main {
  background-color: #92a8d1;
  color: #333333;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  font-family: "Roboto", sans-serif;
  font-size: 16px;
  line-height: 1.5;
}

div {
  background-color: white;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  text-align: center;
}

h4 {
  font-size: 1.5em;
  margin-bottom: 15px;
}

button {
  background-color: white;
  color: black;
  border-radius: 10px;
  border: none;
  font-size: 2em;
  padding: 0.25em 1em;
  margin: 0 1em;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #92a8d1;
  color: white;
}
</style>

<script>
import { ref, computed } from "vue";

export default {
  setup() {
    const count = ref(0);

    const boundedCount = computed(() => {
      return count.value < 0 ? (count.value = 0) : count.value;
    });

    const incrementCount = () => {
      count.value++;
    };

    const decrementCount = () => {
      count.value--;
    };

    return {
      count,
      boundedCount,
      incrementCount,
      decrementCount,
    };
  },
};
</script>
