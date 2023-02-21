<script setup>
const route = useRoute()

const msg = computed(() => `I am on the ${route.params.teamSlug} team and my user id is ${route.params.userId}`)

</script>
<template>
  <div>
    <h1>{{ $route.params.teamSlug }}</h1>
    <p>My user ID is {{ $route.params.userId }}</p>

    <p>
        Here is your message, {{ msg }}
    </p>
  </div>
</template>
