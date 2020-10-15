<template>
  <article :class="['stage', `stage-${color}`]">
    <header>
      <h4>{{ name }}</h4>
      <p>{{ address }}</p>
    </header>
    <ul class="concerts" aria-label="Concerts">
      <li v-for="concert in concerts" :key="concert.time">
        <a :href="concert.tickets" target="_blank" rel="noopener noreferer">
          <span class="concert-time">{{ concert.time }}</span>
          <span class="concert-artist">{{ concert.artist }}</span>
          <span class="concert-icon"><i class="fa fa-ticket" /></span>
        </a>
      </li>
    </ul>
  </article>
</template>

<script>
export default {
  name: 'stage-concerts',

  props: {
    name: {
      type: String,
      required: true
    },
    address: {
      type: String,
      default: ''
    },
    color: {
      type: String,
      default: 'orange'
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

.stage {
  background: $white;
  padding: 1rem;
  border-radius: 1.5rem;

  header {
    background-color: $black;
    padding: 1.5rem;
    border-radius: 1rem;
    margin-bottom: .5rem;

    h4 {
      color: $white;
      font-family: $font-serif;
      text-transform: unset;
      margin-bottom: .5rem;
      font-size: 2.75rem;
      line-height: 1;
    }

    p {
      margin: 0;
      opacity: .75;
      font-family: $font-sans;
      font-size: 1.5rem;
      line-height: 1;
    }
  }

  .concerts {
    list-style: none;
    padding: 1rem;
    padding-bottom: 0;
    margin: 0;

    li {
      border-bottom: 1px #e1e2e3 solid;

      a {
        display: flex;
        padding: .5rem 0;
        font-family: $font-sans;
        color: #53565a;

        &:hover {
          color: $black !important;
          cursor: pointer;
        }

        .concert-time {
          width: 5rem;
        }

        .concert-icon {
          margin-left: auto;
        }
      }

      &:last-child {
        border-bottom: 0;
      }
    }
  }

  @each $name, $color in $colors {
    &.stage-#{$name} {
      header {
        background-color: $color;
      }

      li a {
        color: $color;
      }
    }
  }
}
</style>
