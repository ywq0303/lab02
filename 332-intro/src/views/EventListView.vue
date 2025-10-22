<script setup lang="ts">
import EventCard from '@/components/EventCard.vue'
import type { Event } from '@/type'
import { ref } from 'vue'
const events = ref<Event[]>([
  {
    id: 5928101,
    category: 'animal welfare',
    title: 'Cat Adoption Day',
    description: 'Find your new feline friend at this event.',
    location: 'Meow Town',
    date: 'January 28, 2022',
    time: '12:00',
    petsAllowed: true,
    organizer: 'Kat Laydee'
  },
  {
    id: 4582797,
    category: 'food',
    title: 'Community Gardening',
    description: 'Join us as we tend to the community edible plants.',
    location: 'Flora City',
    date: 'March 14, 2022',
    time: '10:00',
    petsAllowed: true,
    organizer: 'Fern Pollin'
  },
  {
    id: 8419988,
    category: 'sustainability',
    title: 'Beach Cleanup',
    description: 'Help pick up trash along the shore.',
    location: 'Playa Del Carmen',
    date: 'July 22, 2022',
    time: '11:00',
    petsAllowed: false,
    organizer: 'Carey Wales'
  }
])
</script>

<template>
  <h1>Events For Good</h1>
  <!-- new element -->
  
  <!-- 加载状态 -->
  <div v-if="loading" class="loading">
    <p>Loading events...</p>
  </div>
  
  <!-- 错误状态 -->
  <div v-else-if="error" class="error">
    <p>Error: {{ error }}</p>
  </div>
  
  <!-- 空状态 -->
  <div v-else-if="events.length === 0" class="no-events">
    <p>No events found.</p>
  </div>
  
  <!-- 事件列表 -->
  <div v-else class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <p class="event-count">Total events: {{ events.length }}</p>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.loading, .error, .no-events {
  text-align: center;
  padding: 20px;
  margin: 20px 0;
  border-radius: 8px;
}

.loading {
  background-color: #f8f9fa;
  color: #6c757d;
}

.error {
  background-color: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}

.no-events {
  background-color: #e9ecef;
  color: #495057;
}

.event-count {
  margin-top: 20px;
  font-style: italic;
  color: #666;
}
</style>