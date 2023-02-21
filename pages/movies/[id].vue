<script setup>
import { dataToEsm } from '@rollup/pluginutils';


const route = useRoute()

const { data } = await useFetch(
  `http://www.omdbapi.com/?apikey=f2b4b417&i=${route.params.id}`,
  {
    pick: ['Plot', 'Title'],
    // key: route.params.id
    key: `/movies/${route.params.id}`
  }
)

// const { data } = await useAsyncData(() => {
//   return $fetch()
// }, {
//   pick: ['Plot', 'Title'],
//   // transform(data) {
//   //   return {
//   //     Plot: data.Plot,
//   //     Title: data.Title
//   //   }
//   //   return data.Title
//   // }
// })

</script>

<template>
  <div>
    <pre>{{ data }}</pre>
  </div>
</template>

<style scoped></style>