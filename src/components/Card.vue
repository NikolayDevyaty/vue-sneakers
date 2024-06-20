<script setup>
defineProps({
  title: String,
  imgUrl: String,
  price: Number
})
</script>
<template>
  <div>
    <div
      class="relative bg-white border border-slate-100 rounded-3xl p-8 coursor-pointer transition hover:shadow-xl hover:-translate-y-2"
    >
      <img src="/like-2.svg" alt="Like-1" class="absolute top-0 left-8" />
      <img :src="imgUrl" alt="sneakers" />
      <p>{{ title }}</p>
      <div class="flex justify-between mt-5">
        <div class="flex flex-col">
          <span class="text-slate-400">Цена</span>
          <b>{{ price }} руб</b>
        </div>
        <img src="/plus.svg" alt="Plus" />
      </div>
    </div>
  </div>
</template>
