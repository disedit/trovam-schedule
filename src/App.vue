<template>
  <div id="app" class="wrap schedule">
    <div v-for="(day, i) in schedule" :key="day.id" class="day">
      <schedule-day :day="day" />
      <div v-if="i === 1" class="instrument instrument-1">
        <img src="./assets/img/tuba.png" alt="" data-rellax-speed="1.25" class="rellax" />
      </div>
      <div v-if="i === 2" class="instrument instrument-2">
        <img src="./assets/img/drum.png" alt="" data-rellax-speed="1.75" class="rellax" />
      </div>
      <div v-if="i === 3" class="instrument instrument-3">
        <img src="./assets/img/banjo.png" alt="" data-rellax-speed="2" class="rellax" />
      </div>    </div>
  </div>
</template>

<script>
import Rellax from 'rellax'
import ScheduleDay from './components/ScheduleDay.vue'

export default {
  components: {
    ScheduleDay
  },

  data () {
    return {
      schedule: window.schedule
    }
  },

  mounted () {
    const rellax = new Rellax('.rellax')
  }
}
</script>

<style lang="scss">
@import './sass/variables';
@import './sass/tooltips';

.site {
  background-color: $primary;
  color: $text-color;
  transition: background-position .5s;
}

.schedule {
  max-width: 600px;
  margin: 0 auto;
}

.content-wrapper {
  max-width: unset;
  padding-bottom: 0;
}

.content-inner {
  background-color: transparent;
}

.day {
  position: relative;
}

.instrument {
  position: absolute;
  pointer-events: none;
  width: 300px;
  z-index: 1;

  &-1 {
    bottom: -50px;
    transform: translateX(-95%);
  }

  &-2 {
    bottom: 30%;
    transform: translate(590px, 50%);
  }

  &-3 {
    bottom: -15%;
    transform: translateX(-97%);
  }
}

.sidebar-footer,
.site-infos {
  background: transparent !important;
}

@media (max-width: 1200px) {
  .site-main {
    background-position: top left -100px, bottom right -100px;
  }
}

@media (max-width: 700px) {
  #app {
    margin-top: 100px;
  }

  .wrap {
    width: 100%;
  }

  .site {
    background-image: none;
  }

  .site-main {
    background-color: $primary;
  }

  .instrument {
    position: static;
    display: block;
    margin: 0 auto;
    width: 230px;
    transform-origin: top top;
    margin-bottom: -10%;

    &-1 {
      width: 200px;
      transform: translate(-5%, -25%);
    }

    &-2 {
      transform: translate(-8%, -35%);
    }

    &-3 {
      transform: translate(0, -30%);
    }
  }
}
</style>
