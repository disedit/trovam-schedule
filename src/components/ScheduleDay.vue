<template>
  <section class="schedule-day" :aria-labelledby="day.id">
      <h3 :id="day.id"><span>{{ day.label }}</span> <em>{{ day.weekday }}</em></h3>

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
    font-family: $font-rounded;
    color: $yellow;
    font-size: 4rem;
    line-height: 1.1;
    margin-bottom: 2rem;
    text-transform: unset;
    display: flex;
    align-items: center;

    span {
      color: $black;
      border: 2px $black solid;
      background: $magenta;
      font-family: $font-headline;
      font-size: .55em;
      margin-right: 1.4rem;
      padding: .5em .55em .3em .55em;
      border-radius: .5em;
      display: flex;
      align-items: center;
      line-height: 1;
      white-space: nowrap;
      animation: neon 1s infinite;
      --neon-color: #{$yellow};
    }

    em {
      font-style: normal;
      -webkit-text-stroke-width: 2px;
      -webkit-text-stroke-color: $black;
    }
  }
}
</style>
