<template>
  <v-timeline class="mr-6 mx-md-auto" align-top :dense="$vuetify.breakpoint.smAndDown">
    <v-timeline-item
      v-for="item in resume"
      :key="item.slug"
      :color="natures[item.nature].color"
      :icon="natures[item.nature].icon"
      fill-dot
      :left="item.nature === 'pro'"
      :right="item.nature !== 'pro'"
      class="mb-4"
    >
      <v-card
        :color="natures[item.nature].color"
        light
      >
        <v-card-title class="title d-block white--text">
          <p class="mb-0 font-weight-bold">
            {{ item.title }}
          </p>
          <p class="mb-0 caption">
            {{ item.description }}
          </p>
        </v-card-title>
        <v-card-text class="white">
          <nuxt-content class="pt-4" :document="item" />
        </v-card-text>
      </v-card>
    </v-timeline-item>
  </v-timeline>
</template>

<script>
export default {
  props: {
    resume: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      natures: {
        learning: {
          color: 'blue-grey darken-1',
          textClass: 'blue-grey--text text--darken-1',
          icon: 'mdi-book-multiple'
        },
        self: {
          color: 'indigo darken-1',
          textClass: 'indigo--text text--darken-1',
          icon: 'mdi-flask-round-bottom'
        },
        pro: {
          color: 'blue lighten-1',
          textClass: 'blue--text text--lighten-1',
          icon: 'mdi-professional-hexagon'
        }
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.v-timeline {
  max-width: 800px;
}
</style>
