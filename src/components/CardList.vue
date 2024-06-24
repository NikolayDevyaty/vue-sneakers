<script setup>
import { defineEmits } from 'vue'
import Card from './Card.vue'

defineProps({
  items: Array
  // favorites: Array
})
// const onClickAdd = () => {
//   alert('Добавлено в корзину')
// }

const emit = defineEmits(['addToFavorite', 'addToCart'])
// const onCLickFavorite = () => {
//   alert('Добавлено в избранное')
// }

// const addToFavorite = inject('addToFavorite')
// const onCLickFavorite = () => {
//   const obj = {
//     ...props,
//     parentId: props.id //patID
//   }
//   addToFavorite(obj)
// }
</script>
<template>
  <div class="grid grid-cols-2 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :price="item.price"
      :imageUrl="item.imageUrl"
      :onCLickFavorite="() => emit('addToFavorite', item)"
      :onClickAdd="() => emit('addToCart', item)"
      :isFavorite="item.isFavorite"
      :isAdded="item.isAdded"
    />
  </div>
</template>
