<script setup>
import Card from './Card.vue'
// function cardVertical() {
//     return {
//         <Card />
//     }
// }
</script>
<template>
  <div class="grid grid-cols-2 gap-5">
    <Card
      imgUrl="/sneakers/sneakers-1.jpg"
      title="Кроссовки мужские Nike Blazer Mid Suede"
      :price="1200"
    />
    <Card :price="1200" imgUrl="/sneakers/sneakers-2.jpg" title="Кроссовки мужские Nike Blaze" />
    <Card :price="1200" imgUrl="/sneakers/sneakers-3.jpg" title="Кроссовки мужские Nike Blaze" />
    <Card :price="1200" imgUrl="/sneakers/sneakers-4.jpg" title="Кроссовки мужские Nike Blaze" />
    <Card :price="1200" imgUrl="/sneakers/sneakers-5.jpg" title="Кроссовки мужские Nike Blaze" />
    <Card :price="1200" imgUrl="/sneakers/sneakers-6.jpg" title="Кроссовки мужские Nike Blaze" />
  </div>
</template>
