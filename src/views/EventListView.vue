<script setup lang="ts">
import EventCard from '@/components/EventCard.vue'
import EventInfo from '@/components/EventInfo.vue'
import type { Event } from '@/types'
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
  },
  {
    id:20222109,
    category:"social walfare",
    title:"Greeting the elderly",
    description:"Help oderly to do something.",
    location:"Sunshine nursing Home",
    date:"October 13, 2022",
    time:"09:00",
    petsAllowed:false,
    organizer:"Chance"
  }  
])
</script>

<template>
  <h1>Event For Good</h1>
  <!-- new elment -->
<div class="events">
    <div v-for="event in events" :key="event.id" class="event-container">
      <EventCard :event="event" />
      <EventInfo :category="event.category" :organizer="event.organizer" />
    </div>
</div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  
}

.event-container {
  display: flex;
  flex-direction: row; /* 使内容水平排列 */
  justify-content: space-between; /* 使内容两端对齐 */
  width: 100%; /* 根据需要调整宽度 */
  max-width: 600px; /* 设置最大宽度 */
  border: 1px solid #ccc; /* 可选：添加边框 */
  padding: 10px; /* 可选：添加内边距 */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* 可选：添加阴影 */
}
</style>
