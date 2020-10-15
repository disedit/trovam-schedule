<template>
  <div id="app" class="wrap">
    <schedule-day
      v-for="day in schedule"
      :key="day.id"
      :id="day.id"
      :label="day.label"
      :stages="day.stages"
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
      schedule: [
        {
          id: 'Nov11',
          label: 'Dijous, 11 de novembre',
          stages: [
            {
              name: 'Simfònica',
              address: 'Adreça',
              color: 'orange',
              concerts: [
                {
                  time: '19:30',
                  artist: 'Amazonians',
                  tickets: ''
                },
                {
                  time: '20:30',
                  artist: 'Badlands',
                  tickets: ''
                },
                {
                  time: '21:30',
                  artist: 'David Pastor Quartet',
                  tickets: ''
                },
                {
                  time: '22:30',
                  artist: 'Laura Esparza i Carlos Esteban',
                  tickets: ''
                }
              ]
            },
            {
              name: 'Teatre Principal',
              address: 'Adreça',
              color: 'blue',
              concerts: [
                {
                  time: '19:30',
                  artist: 'Amazonians',
                  tickets: ''
                },
                {
                  time: '20:30',
                  artist: 'Badlands',
                  tickets: ''
                }
              ]
            },
            {
              name: 'Escenaria Túria',
              address: 'Adreça',
              color: 'fuchsia',
              concerts: [
                {
                  time: '19:30',
                  artist: 'Amazonians',
                  tickets: ''
                },
                {
                  time: '20:30',
                  artist: 'Badlands',
                  tickets: ''
                },
                {
                  time: '21:30',
                  artist: 'David Pastor Quartet',
                  tickets: ''
                }
              ]
            }
          ]
        },
        {
          id: 'Nov12',
          label: 'Divendres, 12 de novembre',
          stages: [
            {
              name: 'Simfònica',
              address: 'Adreça',
              color: 'red',
              concerts: [
                {
                  time: '19:30',
                  artist: 'Amazonians',
                  tickets: ''
                },
                {
                  time: '20:30',
                  artist: 'Badlands',
                  tickets: ''
                },
                {
                  time: '21:30',
                  artist: 'David Pastor Quartet',
                  tickets: ''
                },
                {
                  time: '22:30',
                  artist: 'Laura Esparza i Carlos Esteban',
                  tickets: ''
                }
              ]
            },
            {
              name: 'Teatre Principal',
              address: 'Adreça',
              color: 'purple',
              concerts: [
                {
                  time: '19:30',
                  artist: 'Amazonians',
                  tickets: ''
                },
                {
                  time: '20:30',
                  artist: 'Badlands',
                  tickets: ''
                }
              ]
            },
            {
              name: 'Escenaria Túria',
              address: 'Adreça',
              color: 'black',
              concerts: [
                {
                  time: '19:30',
                  artist: 'Amazonians',
                  tickets: ''
                },
                {
                  time: '20:30',
                  artist: 'Badlands',
                  tickets: ''
                },
                {
                  time: '21:30',
                  artist: 'David Pastor Quartet',
                  tickets: ''
                }
              ]
            }
          ]
        }
      ]
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
