<script setup lang="ts">
import {useQuery} from "@tanstack/vue-query"
import ToDo from '@/components/ToDo.vue'

const getTodos = async () => {
  return await fetch('https://jsonplaceholder.cypress.io/users/1/todos').then((response) =>
      response.json(),
  )
}

const {data, suspense} = useQuery({
  queryKey: ['todos'],
  queryFn: getTodos,
})

await suspense()

</script>
<template>

  <div v-if="data">
    <div>
      <ul>
        <li v-for="todo in data" :key="todo.id">
          {{ todo.title }}
          <ToDo :id="todo.id"/>
        </li>
      </ul>
    </div>
  </div>
</template>
