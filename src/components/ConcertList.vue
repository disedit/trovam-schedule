<template>
  <ul class="concerts" :aria-labelledby="id">
    <li v-for="concert in concerts" :key="concert.time">
      <component
        :is="concert.url ? 'a' : 'div'"
        :href="concert.url"
        :class="`concert stage-${concert.stage} concert-color--${stage('color', concert.stage)}`">
        <span class="concert-time">{{ concert.time }}</span>
        <span class="concert-artist">
          {{ concert.artist }}
          <span class="concert-artist-text" v-if="concert.text">
            {{ concert.text }}
          </span>
        </span>
        <span v-if="concert.stage" class="concert-stage" v-tooltip="stage('venue', concert.stage)">
          {{ stage('label', concert.stage) }}
          <span class="concert-stage-venue" v-if="stage('venue', concert.stage)">- {{ stage('venue', concert.stage) }}</span>
        </span>
        <span class="concert-icon"><i class="fa fa-ticket" v-tooltip="'Entrades'" v-if="concert.tickets" /></span>
      </component>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'concert-list',

  props: {
    id: {
      type: String,
      required: true
    },
    concerts: {
      type: Array,
      required: true
    }
  },

  data () {
    return {
      stages: {
        simfonica: {
          label: 'Sala Simfònica',
          venue: 'Auditori de Castelló',
          color: 'purple'
        },
        turia: {
          label: 'Escenari Túria',
          venue: 'Auditori de Castelló',
          color: 'blue'
        },
        hotelintur: {
          label: 'Hotel Intur',
          color: 'orange'
        },
        magicbox: {
          label: 'Magic Box',
          venue: 'Auditori de Castelló',
          color: 'blue'
        },
        cambra: {
          label: 'Sala de Cambra',
          venue: 'Auditori de Castelló',
          color: 'orange'
        },
        apunt: {
          label: 'Teatre Principal',
          venue: 'Castelló',
          color: 'magenta'
        },
        hort: {
          label: 'Hort dels Corders',
          venue: 'Plaça Hort dels Corders',
          color: 'purple'
        },
        aularis: {
          label: 'Aularis',
          venue: 'Auditori de Castelló',
          color: 'gray'
        },
        premsa: {
          label: 'Sala de premsa',
          venue: 'Auditori de Castelló',
          color: 'gray'
        },
        raval: {
          label: 'Teatre del Raval',
          color: 'orange'
        },
        stream: {
          label: 'Streaming',
          color: 'orange'
        },
        ajornat: {
          label: 'Ajornat',
          color: 'black'
        },
        cancelled: {
          label: 'Cancel·lat',
          color: 'black'
        },
        terra: {
          label: 'Pub Terra',
          color: 'orange'
        },
        hotel: {
          label: 'Hotel del Golf Playa',
          color: 'yellow'
        },
        paranimf: {
          label: 'Paranimf UJI',
          color: 'green'
        },
        arts: {
          label: 'Passadís de les Arts',
          venue: 'Parc Ribalta',
          color: 'magenta'
        },
        pati: {
          label: 'Pati',
          venue: 'Auditori de Castelló',
          color: 'green'
        },
        templet: {
          label: 'Templet',
          venue: 'Parc Ribalta',
          color: 'blue'
        }
      }
    }
  },

  methods: {
    stage (prop, stage) {
      return stage in this.stages ? this.stages[stage][prop] : null
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../sass/variables';

.concerts {
  position: relative;
  list-style: none;
  padding: 0 1.25rem;
  margin: 3rem 0;
  background: $white;
  border-radius: 1rem;

  &::before {
    position: absolute;
    content: '';
    top: -1rem;
    left: -1rem;
    right: -1rem;
    bottom: -1rem;
    border: 3px $green solid;
    border-radius: 1.75rem;
    pointer-events: none;
    --neon-color: #{$green};
    animation: neon 2s infinite;
    animation-delay: 1s;
  }

  &::after {
    position: absolute;
    content: '';
    top: -2rem;
    left: -2rem;
    right: -2rem;
    bottom: -2rem;
    border: 3px $blue solid;
    border-radius: 2.75rem;
    pointer-events: none;
    --neon-color: #{$blue};
    animation: neon 2s infinite;
  }

  li {
    border-bottom: 1px #e1e2e3 solid;

    .concert {
      display: grid;
      grid-template-columns: 45px 1fr 150px 20px;
      grid-template-areas: "time artist stage icon";
      gap: 1rem;
      padding: .75rem 1.25rem;
      margin: -1px -1.25rem;
      font-family: $font-sans;
      font-weight: bold;
      color: #53565a;
      transition: .1s ease;
      line-height: 1.2;

      .concert-time {
        grid-area: time;
        padding: .5rem 0;
      }

      .concert-artist {
        grid-area: artist;
        padding: .5rem 0;

        &-text {
          font-weight: normal;

          &::before {
            content: ' / ';
            opacity: .5;
          }
        }
      }

      .concert-stage {
        grid-area: stage;
        background-color: $black;
        color: $white;
        border-radius: .5rem;
        padding: .5rem 1rem;
        text-align: center;
        align-self: start;

        &-venue {
          display: none;
        }
      }

      .concert-icon {
        grid-area: icon;
        padding: .5rem 0;
        text-align: right;
      }
    }

    a.concert {
      &:hover {
        color: $black;
      }
    }

    &:first-child {
      .concert {
        padding-top: 1.25rem;
        border-radius: 1rem 1rem 0 0;
      }
    }

    &:last-child {
      border-bottom: 0;

      .concert {
        padding-bottom: 1.25rem;
        border-radius: 0 0 1rem 1rem;
      }
    }

    @each $name, $color in $colors {
      .concert-color--#{$name} {
        .concert-stage {
          background-color: $color;
        }
      }

      a.concert-color--#{$name} {
        &:hover {
          background: mix($color, $white, 10%) !important;
          color: $color !important;
        }

        &:active {
          background: mix($color, $white, 20%) !important;
        }
      }
    }

    .stage-cancelled {
      text-decoration: line-through;
      text-decoration-color: #FA353E;
      text-decoration-thickness: 2px;
    }
  }
}

@media (max-width: 700px) {
  .concerts {
    li {
      .concert {
        grid-template-columns: 45px 1fr 100px;
        grid-template-areas:
          "time artist icon"
          "stage stage stage";
        row-gap: .5rem;

        &-stage-venue {
          display: inline !important;
        }
      }

      @each $name, $color in $colors {
        .concert-color--#{$name} {
          .concert-stage {
            background-color: mix($color, $white, 15%);
            color: darken($color, 10%);
          }
        }
      }
    }
  }
}

@keyframes neon {
  0% {
    filter: drop-shadow(0 0 0 var(--neon-color));
  }

  24% {
    filter: drop-shadow(0 0 0 var(--neon-color));
  }

  25% {
    filter: drop-shadow(0 0 4px var(--neon-color)) drop-shadow(0 0 10px var(--neon-color)) drop-shadow(0 0 20px var(--neon-color));
  }

  75% {
    filter: drop-shadow(0 0 4px var(--neon-color)) drop-shadow(0 0 10px var(--neon-color)) drop-shadow(0 0 20px var(--neon-color));
  }

  76% {
    filter: drop-shadow(0 0 0 var(--neon-color));
  }

  100% {
    filter: drop-shadow(0 0 0 var(--neon-color));
  }
}
</style>
