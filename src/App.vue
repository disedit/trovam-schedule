<template>
  <div id="app" class="wrap schedule">
    <div v-for="day in schedule" :key="day.id" class="day">
      <schedule-day :day="day" />
    </div>
  </div>
</template>

<script>
import ScheduleDay from './components/ScheduleDay.vue'

export default {
  components: {
    ScheduleDay
  },

  data () {
    return {
      schedule: window.schedule
    }
  }
}
</script>

<style lang="scss">
@import './sass/variables';
@import './sass/tooltips';

@font-face {
    font-family: 'giuliobold';
    src: url('./assets/fonts/giulio-bold-webfont.woff2') format('woff2'),
         url('./assets/fonts/giulio-bold-webfont.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

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
