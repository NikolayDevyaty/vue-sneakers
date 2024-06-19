<script setup>
defineProps({
  title: String,
  price: Number,
  isAdded: Boolean
})
</script>

<template>
  <div class="product">
    <h2>
      Товар: {{ title }}
    </h2>
    <h3>
      Цена: {{ price }}
    </h3>
    <h3>
      Добавлен: {{ isAdded }}
    </h3>
    <slot></slot>
  </div>
</template>

<style scoped>
.product {
  border: 1px solid blue;
  padding: 10px;
  margin-bottom: 10px;
}

/* h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
} */
</style>
