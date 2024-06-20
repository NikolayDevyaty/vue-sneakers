<script setup>
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
</script>

<template>
  <div class="bg-white w-4/5 m-auto rounded-xl mt-14 shadow-xl">
    <Header />
    <div class="p-10">
      <h2 class="text-3xl font-bold px-8">Все кроссовки</h2>
      <CardList/>
    </div>

    <h1>Blog</h1>
  </div>
</template>

<style scoped></style>
