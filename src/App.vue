<script setup lang="ts">
import ToDos from '@/components/ToDos.vue'
</script>
<template>
  <Suspense>
    <ToDos/>
    <template #fallback>
      <div>Loading in progress ...</div>
    </template>
  </Suspense>
</template>
