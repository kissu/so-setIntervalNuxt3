<script setup>
import { useIntervalFn } from '@vueuse/core' // VueUse helper, install it

const { pending, data, error, refresh } = await useFetch('https://jsonplaceholder.typicode.com/todos/1')

useIntervalFn(() => {
  console.log(`refreshing the data again ${new Date().toISOString()}`)
  refresh() // will call the 'todos' endpoint, just above
}, 3000) // call it back every 3s
</script>

<template>
  <div v-if="!pending">
    <pre>{{ data }}</pre>
  </div>
</template>
