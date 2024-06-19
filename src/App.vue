<script setup>
import MyHello from './components/MyHello.vue';
</script>

<template>
  <MyHello title="Puma" :price="10000" :isAdded="true">
    <button>Купить</button>
  </MyHello>
  <MyHello />
  <MyHello />
  <MyHello />
</template>

<style scoped></style>
