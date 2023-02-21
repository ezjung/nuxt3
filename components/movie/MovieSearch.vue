<script setup>

  const query = ref("batman")
  const movies = ref([])

  async function search() {
    const { Search } = await $fetch(`http://www.omdbapi.com/?apikey=f2b4b417&s=${query.value}`)
    movies.value = Search
  }

  search()

</script>

<template>
  <div class="mx-24">

    <form @submit.prevent="search" class="flex justify-center">
      <input type="text" v-model="query" class="border mr-4">
      <button>Search</button>
    </form>
    <ul class="grid grid-cols-4 wrap gap-x-4 gap-y-4 mt-16">
      <li v-for="movie in movies" :key="movie.imdbID">
        <NuxtLink :to="{ name: 'movies-id', params: { id: movie.imdbID } }">
          <img :src="movie.Poster" :alt="movie.title" class="h-200 w-200 overflow-hidden">
        </NuxtLink>
      </li>
    </ul>    
  </div>

</template>