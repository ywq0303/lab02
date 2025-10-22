<script setup lang="ts">
import type { Event } from '@/type'

defineProps<{
  event: Event
}>()
</script>

<template>
  <div class="category-organizer-card">
    <p>Category: {{ event.category }}</p>
    <p>Organizer: {{ event.organizer }}</p>
  </div>
</template>

<style scoped>
.category-organizer-card {
  text-align: right;
  margin: 10px 0;
}

.category-organizer-card p {
  margin: 5px 0;
  font-size: 14px;
}
</style>