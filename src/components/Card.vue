<script setup>
defineProps({
  title: String,
  imageUrl: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onCLickAdded: Function,
  onCLickFavorite: Function
})
</script>
<template>

    <div
      class="relative bg-white border border-slate-100 rounded-3xl p-8 coursor-pointer transition hover:shadow-xl hover:-translate-y-2"
    >
      <img
        :src="isFavorite ? '/like-2.svg' : '/like-1.svg'"
        alt="Like-1"
        class="absolute top-0 left-8"
        @click="onCLickFavorite"
      />
      <img :src="imageUrl" alt="sneakers" />
      <p>{{ title }}</p>
      <div class="flex justify-between mt-5">
        <div class="flex flex-col">
          <span class="text-slate-400">Цена</span>
          <b>{{ price }} руб</b>
        </div>
        <img :src="isAdded ? '/checked.svg' : ' /plus.svg'" alt="Plus" @click="onCLickAdded" />
      </div>
    </div>
</template>
