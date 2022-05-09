<template>
  <div class="events">
    <h1>Events For Good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
// import axios from 'axios';
import EventService from '@/services/EventService.js'

export default {
  name: 'Home',
  components: {
    EventCard
  },
  data() {
    return {
      events: null
    }
  },
  async created() {
    try {
      let response = await EventService.getEvents()
      this.events = await response.data
    } catch (error) {
      console.log(error)
    }
  }
}
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
