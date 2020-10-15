<template>
  <section class="schedule-day" :aria-labelledby="id">
      <h3 :id="id">{{ label }}</h3>
      <div class="stages">
        <stage-concerts
          v-for="stage in stages"
          :key="stage.name"
          :name="stage.name"
          :address="stage.address"
          :color="stage.color"
          :concerts="stage.concerts" />
      </div>
    </section>
</template>

<script>
import StageConcerts from './StageConcerts.vue'

export default {
  name: 'schedule-day',

  components: {
    StageConcerts
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
    stages: {
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
    font-family: $font-sans;
    color: $white;
    font-size: 4rem;
    line-height: 1.1;
    margin-bottom: 2rem;
  }

  .stages {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 4rem;
    align-items: start;
  }
}
</style>
