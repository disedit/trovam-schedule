<template>
  <div id="app" class="wrap schedule">
    <schedule-day
      v-for="day in schedule"
      :key="day.id"
      :id="day.id"
      :label="day.label"
      :concerts="day.concerts"
    />
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

.site-main {
  background-color: $primary;
  background-image: url(./assets/img/chopsticks.jpg), url(./assets/img/earpods.jpg);
  background-size: 380px, 400px;
  background-repeat: no-repeat;
  background-position: top left, bottom right;
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

.sidebar-footer,
.site-infos {
  background: $primary !important;
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

  .site-main {
    background-position: top -180px left -200px, bottom right;
    padding-top: 100px;
    padding-bottom: 400px;
  }
}
</style>
