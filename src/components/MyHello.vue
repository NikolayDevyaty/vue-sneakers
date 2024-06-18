<script setup>
import { ref } from 'vue'
let count = ref(50)

function increment() {
  count.value++
  console.log(count)
}
function inputVal(val) {
  count.value = val.target.value
  console.log(count)
}
</script>

<template>
  <h1>
    {{ count }}
  </h1>
  <button @click="increment">+</button>
  <!-- <input @input="inputVal" key="count" type="number" /> -->
  <input @keyup.ctrl.enter="increment" key="count" type="number" />
</template>

<!-- <style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style> -->
