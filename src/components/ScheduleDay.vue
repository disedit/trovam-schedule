<template>
  <section class="schedule-day" :aria-labelledby="id">
      <h3 :id="id">{{ label }}</h3>

      <concert-list :id="id" :concerts="concerts" />
    </section>
</template>

<script>
import ConcertList from './ConcertList.vue'

export default {
  name: 'schedule-day',

  components: {
    ConcertList
  },

  props: {
    id: {
      type: String,
      required: true
    },
    label: {
      type: String,
      required: true
    },
    concerts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../sass/variables';

.schedule-day {
  margin-bottom: 8rem;

  h3 {
    font-family: $font-serif;
    color: $white;
    font-size: 4rem;
    line-height: 1.1;
    margin-bottom: 2rem;
    text-transform: unset;
  }
}

@media (max-width: 700px) {
  .schedule-day {
    h3 {
      font-size: 3rem;
    }
  }
}
</style>
