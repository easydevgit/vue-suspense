<script setup lang="ts">
import {useQuery} from "@tanstack/vue-query"

const props = defineProps({
  id: {type: Number, required: true}
})

const getTodo = async (id: number) => {
  return await fetch(`https://jsonplaceholder.cypress.io/todos/${id}`).then((response) =>
      response.json(),
  )
}

const {data, suspense} = useQuery({
  queryKey: ['todo', props.id],
  queryFn: () => getTodo(props.id),
})

await suspense()

</script>

<template>
  <div v-if="data"> {{ data.body }}</div>
</template>
