<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from '@/services/EventService.js'

export default {
  props: ['id'],
  data() {
    return {
      event: null,
      // id: 123,
    }
  },
  async created() {
    // fetch event (by id) and set local event data
    try {
      const res = await EventService.getEvent(this.id);
      this.event = await res.data;
    } catch (error) {
      console.log(error);
    }
    // const res = await EventService.getEvent(this.id)
    // this.event = res.data
  }
}
</script>
      