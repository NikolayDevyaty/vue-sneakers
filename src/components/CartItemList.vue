<script setup>
import CartItem from './CartItem.vue'
import { inject } from 'vue'

const { cart, addToCart } = inject('cart')
</script>

<template>
  <div class="grid grid-cols-1 gap-5">
    <CartItem
      v-for="item in cart"
      :key="item.id"
      :title="item.title"
      :price="item.price"
      :image-url="item.imageUrl"
      :onClick="() => addToCart(item)"
    />
  </div>
</template>
