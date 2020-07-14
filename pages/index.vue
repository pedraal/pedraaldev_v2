<template>
  <div>
    <app-card />
    <app-timeline :resume="resume" class="app-timeline" />
  </div>
</template>

<script>
import AppCard from '@/components/AppCard'
import AppTimeline from '@/components/AppTimeline'
export default {
  transition: {
    name: 'fade',
    mode: 'out-in'
  },
  components: {
    AppCard,
    AppTimeline
  },
  async asyncData ({ $content, params }) {
    const resume = await $content('resume')
      .sortBy('order', 'asc')
      .fetch()

    return { resume }
  }
}
</script>

<style lang="scss" scoped>
.placeholder {
  min-height: 900px;
}
</style>

<style>
.fade-enter-active, .fade-leave-active {
  transition: all .2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
