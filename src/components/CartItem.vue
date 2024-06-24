<script setup>
defineProps({
  id: Number,
  title: String,
  imageUrl: String,
  price: Number,
  onCLick: Function
})
</script>

<template>
  <div class="items-center flex border border-slate-200 p-4 rounded-xl">
    <img class="w-16 h-16" :src="imageUrl" :alt="title" />

    <div class="flex flex-col flex-1">
      <p>{{ title }}</p>

      <div class="flex justify-between mt-2">
        <b class="flex-1">{{ price }} руб</b>
        <img
          @click="onCLick"
          class="opacity-50 hover:opacity-100 coursor-pointer transition"
          src="/close.svg"
          alt="close"
        />
      </div>
    </div>
  </div>
</template>
