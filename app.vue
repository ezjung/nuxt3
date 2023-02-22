<script setup>
useHead({
  titleTemplate: (pageTitle) => {
    return pageTitle ? `My movie site:${pageTitle}` : 'My movie site'
  }
})
</script>

<template>
  <div>
    <nav class="flex justify-center gap-4 text-xl">
      <!-- 
        
        /movies/id:123 
      
      -->
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/movies">Movies</NuxtLink>
      <NuxtLink to="https://codeforkitchen.com">Umami</NuxtLink>
    </nav>
    <NuxtPage />
  </div>
</template>
