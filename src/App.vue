<script setup>
import { ref, watch, provide, computed } from 'vue'
import axios from 'axios'
import Header from './components/Header.vue'
import Drawer from './components/Drawer.vue'
import Home from './pages/Home.vue'

const cart = ref([])
const drawerOpen = ref(false)
const isCreatedOrder = ref(false)

const totalPrice = computed(() => cart.value.reduce((acc, item) => (acc += item.price), 0))
const tax = computed(() => Math.round(totalPrice.value / 100) * 5)

/*Корзина Начало*/
const closeDrawer = () => {
  drawerOpen.value = false
}
const openDrawer = () => {
  drawerOpen.value = true
}

const createOrder = async () => {
  try {
    isCreatedOrder.value = true
    const { data } = await axios.post('https://2155c769805dbec6.mokky.dev/orders', {
      items: cart.value,
      total: totalPrice.value
    })
    cart.value = []
    return data
  } catch (error) {
    console.log(error)
  } finally {
    isCreatedOrder.value = false
  }
}

const addToCartPlus = (item) => {
  cart.value.push(item)
  item.isAdded = true
}
const removeFromCart = (item) => {
  cart.value.splice(cart.value.indexOf(item), 1)
  item.isAdded = false
}
const addToCart = (item) => {
  console.log(cart)
  if (!item.isAdded) {
    addToCartPlus(item)
  } else {
    removeFromCart(item)
  }
}

provide('cart', { cart, openDrawer, closeDrawer, addToCart, removeFromCart })

watch(
  cart,
  () => {
    localStorage.setItem('cart', JSON.stringify(cart.value))
  },
  { deep: true }
)
/*Корзина Конец*/
</script>

<template>
  <Drawer
    :total="totalPrice"
    :tax="tax"
    v-if="drawerOpen"
    @create-order="createOrder"
    :is-created-order="isCreatedOrder"
  />
  <div class="bg-white w-4/5 m-auto rounded-xl mt-14 shadow-xl">
    <Header :total="totalPrice" @open-drawer="openDrawer" />
    <div class="p-10">
      <Home @add-to-cart="addToCart" />
    </div>
  </div>
</template>

<style scoped></style>
