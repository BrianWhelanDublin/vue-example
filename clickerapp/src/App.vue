<template>
  <h2>{{ state.count }}, doubled = {{ state.double }}</h2>
  <button @click="UpdateCount(true)">+</button>
  <button @click="UpdateCount(false)">-</button>
</template>

<script>
import { reactive, computed } from "vue";

export default {
  setup() {
    const state = reactive({
      count: 0,
      double: computed(() => state.count * 2),
    });
    function UpdateCount(increase) {
      increase ? state.count++ : state.count--;
    }
    return {
      state,
      UpdateCount,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  height: 20px;
  width: 40px;
}
</style>
