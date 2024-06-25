<script setup>
import CartItem from './CartItem.vue'
import { inject } from 'vue'

const { cart, removeFromCart } = inject('cart')
</script>

<template>
  <div class="grid grid-cols-1 gap-5" v-auto-animate>
    <CartItem
      v-for="item in cart"
      :key="item.id"
      :title="item.title"
      :price="item.price"
      :image-url="item.imageUrl"
      @onClickRemove="() => removeFromCart(item)"
    />
  </div>
</template>
