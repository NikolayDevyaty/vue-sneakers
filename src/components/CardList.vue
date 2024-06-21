<script setup>
import Card from './Card.vue'
defineProps({
  items: Array
})
// const onCLickAdded = () => {
//   alert('Добавлено в корзину')
// }
// const onCLickFavorite = () => {
//   alert('Добавлено в избранное')
// }
</script>
<template>
  <div class="grid grid-cols-2 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :price="item.price"
      :imageUrl="item.imageUrl"
    />
  </div>
</template>
