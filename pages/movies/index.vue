<script setup>
  const query = ref("")
  const movies = ref([])

  async function search() {
    const { Search } = await $fetch(`http://www.omdbapi.com/?i=tt3896198&apikey=f2b4b417&s=${query.value}`)
    movies.value = Search
  }

</script>

<template>
  <form @submit.prevent="search" class="flex justify-center">
    <input type="text" v-model="query" class="border mr-4">
    <button>Search</button>
  </form>
  <ul class="flex wrap gap-10">
    <li v-for="movie in movies" :key="movie.imdbID">
      <NuxtLink :to="{ name: 'movies-id', params: { id: movie.imdbID } }">
        <img :src="movie.Poster" :alt="movie.title" class="h-40 w-40 overflow-hidden">
      </NuxtLink>
    </li>
  </ul>
</template>

<style scoped></style>