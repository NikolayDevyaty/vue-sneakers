<script setup>
import axios from 'axios'
import { inject, reactive, watch, ref, onMounted } from 'vue'
import CardList from '../components/CardList.vue'

const items = ref([])
const filters = reactive({
  searchQuery: '',
  sortBy: 'title'
})

const { cart, addToCart } = inject('cart')
const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value
}

const addToFavorite = async (item) => {
  try {
    if (!item.isFavorite) {
      const obj = {
        parentId: item.id
      }
      item.isFavorite = true
      const { data } = await axios.post(`https://2155c769805dbec6.mokky.dev/favorites`, obj)

      item.favoriteId = data.id
      console.log(data)
    } else {
      item.isFavorite = false
      await axios.delete(`https://2155c769805dbec6.mokky.dev/favorites/${item.favoriteId}`)

      item.favoriteId = null
    }
  } catch (error) {
    console.log(error)
  }
}

const fetchFavorites = async () => {
  try {
    const { data: favorites } = await axios.get(`https://2155c769805dbec6.mokky.dev/favorites`)
    items.value = items.value.map((item) => {
      const favorite = favorites.find((favorite) => favorite.parentId === item.id)
      if (!favorite) {
        return item
      }
      return { ...item, isFavorite: true, favoriteId: favorite.id }
    })
    console.log(items.value)
  } catch (error) {
    console.log(error)
  }
}
const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy
    }
    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }
    const { data } = await axios.get(`https://2155c769805dbec6.mokky.dev/items`, { params })
    // const { favData } = await axios.get(`https://2155c769805dbec6.mokky.dev/favorites`)
    items.value = data.map((obj) => ({
      ...obj,
      isFavorite: false,
      favoriteId: null,
      isAdded: false
    }))

    console.log(items.value)
  } catch (error) {
    console.log(error)
  }
}

onMounted(async () => {
  const localCart = localStorage.getItem('cart')
  cart.value = localCart ? JSON.parse(localCart) : []
  await fetchItems()
  await fetchFavorites()

  items.value = items.value.map((item) => ({
    ...item,
    isAdded: cart.value.some((cartItem) => cartItem.id === item.id)
  }))
})

watch(filters, fetchItems)

watch(cart, () => {
  items.value = items.value.map((item) => ({ ...item, isAdded: false }))
})
</script>
<template>
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
        @input="onChangeSearchInput"
        type="text"
        placeholder="Поиск..."
        class="border rounded py-1 px-2 pl-10 pr-5 outline-none focus:border-gray-400"
      />
    </div>
  </div>
  <div class="mt-10">
    <CardList :items="items" @addToFavorite="addToFavorite" @addToCart="addToCart" />
  </div>
</template>
