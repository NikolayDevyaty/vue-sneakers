<script setup>
import Card from './Card.vue'
const onCLickAdded = () => {
  alert('Добавлено в корзину')
}
const onCLickFavorite = () => {
  alert('Добавлено в избранное')
}
</script>
<template>
  <div class="grid grid-cols-2 gap-5">
    <Card
      :isAdded="false"
      :isFavorite="false"
      imgUrl="/sneakers/sneakers-1.jpg"
      title="Кроссовки мужские Nike Blazer Mid Suede"
      :price="1200"
      :onCLickAdded="onCLickAdded"
      :onCLickFavorite="onCLickFavorite"
    />
    <Card :price="1200" imgUrl="/sneakers/sneakers-2.jpg" title="Кроссовки мужские Nike Blaze" />
    <Card :price="1200" imgUrl="/sneakers/sneakers-3.jpg" title="Кроссовки мужские Nike Blaze" />
    <Card :price="1200" imgUrl="/sneakers/sneakers-4.jpg" title="Кроссовки мужские Nike Blaze" />
    <Card :price="1200" imgUrl="/sneakers/sneakers-5.jpg" title="Кроссовки мужские Nike Blaze" />
    <Card :price="1200" imgUrl="/sneakers/sneakers-6.jpg" title="Кроссовки мужские Nike Blaze" />
  </div>
</template>
