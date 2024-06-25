<script setup>
defineProps({
  title: String,
  description: String,
  imageUrl: String
})
</script>
<template>
  <div class="text-center flex flex-col items-center w-72 mx-auto">
    <img height="90" width="90" :src="imageUrl" alt="Info Image" />
    <h2 class="mt-4 text-2xl font-medium">{{ title }}</h2>
    <p class="mt-4 text-slate-400">{{ description }}</p>
  </div>
</template>
