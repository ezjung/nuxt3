<script setup>

const route = useRoute()

const { data } = await useAsyncData(() => {
  return $fetch(`http://www.omdbapi.com/?apikey=f2b4b417&i=${route.params.id}`)
})

</script>

<template>
  <div>
    <pre>{{ data }}</pre>
  </div>
</template>

<style scoped></style>