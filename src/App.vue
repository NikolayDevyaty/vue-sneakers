<script setup>
import { onMounted, ref, watch } from 'vue'
import axios from 'axios'
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
// import Drawer from './components/Drawer.vue'
const items = ref([])
const sortBy = ref('')
const onChangeSelect = (event) => {
  sortBy.value = event.target.value
}
// const items = [
//   { id: 1, title: 'Кроссовки мужские', price: 9000, imageUrl: '/sneakers/sneakers-1.jpg' },
//   { id: 2, title: 'Кроссовки женские', price: 9000, imageUrl: '/sneakers/sneakers-2.jpg' },
//   { id: 3, title: 'Кроссовки детские', price: 9000, imageUrl: '/sneakers/sneakers-3.jpg' }
// ]
onMounted(async () => {
  try {
    const { data } = await axios.get('https://2155c769805dbec6.mokky.dev/items')
    items.value = data
  } catch (error) {
    console.log(error)
  }
})

watch(sortBy, async () => {
  try {
    const { data } = await axios.get(
      'https://2155c769805dbec6.mokky.dev/items?sortBy=' + sortBy.value
    )
    items.value = data
  } catch (error) {
    console.log(error)
  }
})
</script>

<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl mt-14 shadow-xl">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold px-8">Все кроссовки</h2>
        <div class="flex gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none" id="">
            <option value="name">По названию</option>
            <option value="price">По цене (дешевле)</option>
            <option value="-price">По цене (дороже)</option>
          </select>
        </div>

        <div class="relative">
          <img class="absolute left-4 top-3" src="/search.svg" />
          <input
            type="text"
            placeholder="Поиск..."
            class="border rounded py-1 px-2 pl-10 pr-5 outline-none focus:border-gray-400"
          />
        </div>
      </div>
      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
