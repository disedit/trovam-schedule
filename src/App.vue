<template>
  <div id="app" class="wrap">
    <stage-concerts />
  </div>
</template>

<script>
import StageConcerts from './components/StageConcerts'

export default {
  components: {
    StageConcerts
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

.site-main {
  background-color: $primary;
  background-image: url(./assets/img/chopsticks.jpg), url(./assets/img/earpods.jpg);
  background-size: 380px, 400px;
  background-repeat: no-repeat;
  background-position: top left, bottom right;
  color: $text-color;
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

@media (max-width: 700px) {
  #app {
    margin-top: 100px;
  }
}
</style>
