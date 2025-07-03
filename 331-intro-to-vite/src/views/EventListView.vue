<script setup lang="ts">
import EventMeta from '@/components/EventMeta.vue'
import { Event } from '@/types'
import { ref,onMounted } from 'vue'
import axios from 'axios'

const events=ref<Event[]>(null)

onMounted(() => {
  axios
    .get('https://my-json-server.typicode.com/Hninei-Shweyee/mock-events/events')
    .then((response) => {
      events.value=response.data
    })
    .catch((error) => {
      console.error('There was an error!', error)
    })
})
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventMeta v-for="event in events" :key="event.id" :event="event"/>

  </div>
</template>
<style scoped>
.events{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
