<template>
  <section class="schedule-day" :aria-labelledby="day.id">
      <h3 :id="day.id"><span>{{ day.label }}</span> {{ day.weekday }}</h3>

      <concert-list :id="day.id" :concerts="day.concerts" />
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
    day: {
      type: Object,
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
    display: flex;
    align-items: center;

    span {
      color: $secondary;
      border: 3px currentColor solid;
      font-family: $font-sans;
      font-size: .55em;
      margin-right: 1rem;
      padding: .5em .55em .6em .55em;
      border-radius: 50%;
      display: flex;
      align-items: center;
      line-height: 1;
      white-space: nowrap;
    }
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
