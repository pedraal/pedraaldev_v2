<template>
  <v-app>
    <v-main class="mt-4">
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer
      absolute
      app
      class="d-none d-md-block"
    >
      <span>PedraalDev &copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {

}
</script>
