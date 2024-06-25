<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue'
import infoBlock from './infoBlock.vue'
import { computed } from 'vue'

computed
const emit = defineEmits(['createOrder'])
const props = defineProps({
  total: Number,
  tax: Number,
  isCreatedOrder: Boolean
})
const buttonDisabled = computed(() => (props.isCreatedOrder ? true : props.total ? false : true))
</script>

<template>
  <div class="fixed top-0 left-0 w-full h-full bg-black z-10 opacity-70 transition-all"></div>
  <div class="bg-white w-96 h-full fixed top-0 right-0 z-20 p-8">
    <DrawerHead />
    <div v-if="total === 0" class="flex h-full items-center">
      <infoBlock
        title="Корзина пуста"
        description="Добавьте хотя бы одну пару кроссовок, чтобы сделать заказ."
        imageUrl="/package-icon.png"
      />
    </div>
    <div v-else>
      <CartItemList />
      <div class="flex flex-col gap-5 mt-7">
        <div class="flex gap-2">
          <span> Итого: </span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ total }} руб</b>
        </div>

        <div class="flex gap-2">
          <span> Налог 5%: </span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ tax }} руб</b>
        </div>
      </div>

      <button
        :disabled="buttonDisabled"
        @click="emit('createOrder')"
        class="coursir-pointer disabled:bg-slate-300 disabled:slate-400 disabled:transition w-full bg-lime-500 text-white rounded-xl py-3 mt-7 hover:bg-lime-600 active:bg-lime-700"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>
