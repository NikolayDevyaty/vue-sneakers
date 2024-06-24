<script setup></script>

<template>
  <div class="items-center flex border border-slate-200 p-4 rounded-xl">
    <img class="w-16 h-16" src="/sneakers/sneakers-1.jpg" alt="sneakers" />

    <div class="flex flex-col">
      <p>Кроссовки мужские NIKE Blazer Mid Suede</p>

      <div class="flex justify-between mt-2">
        <b>1200 руб</b>
        <img
          emit
          class="opacity-50 hover:opacity-100 coursor-pointer transition"
          src="/close.svg"
          alt="close"
        />
      </div>
    </div>
  </div>
</template>
