<script setup>
import { dataToEsm } from '@rollup/pluginutils';


const route = useRoute()

const { data } = await useFetch(
  `http://www.omdbapi.com/?apikey=f2b4b417&i=${route.params.id}`,
  {
    pick: ['Plot', 'Title', 'Poster', 'Error'],
    // key: route.params.id
    key: `/movies/${route.params.id}`,


    // onResponse({request, response}) {
    //   console.log(response)

    //   if(response._data.Response == "False") {
    //     showError({ statusCode: 404, statusMessage: "Page Not Found" })
    //   }
    // }
  }
)

if (data.value.Error === "Incorrect IMDb ID.") {
  showError({ statusCode: 404, statusMessage: "Page Not Found" })
}

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

useHead({
  // title: "Hello page",
  title: data.value.Title,
  meta: [
    { name: "description", content: data.value.Plot },
    { property: "og:description", content: data.value.Plot },
    { property: "og:image", content: data.value.Poster },
    { name: "twitter:card", content: `summary_large_image` },
  ],
})

</script>

<template>
  <div>
    <pre>{{ data }}</pre>
  </div>
</template>

<style scoped></style>