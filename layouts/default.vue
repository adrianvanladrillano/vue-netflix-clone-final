
<template>
  <v-app>
    <netflix-nav-mobile
      :type="$route.name == 'app-id' ? 'main' : 'sub'"
      v-if="$vuetify.breakpoint.mobile"
    />
    <netflix-nav-desktop
      v-if="!$vuetify.breakpoint.mobile"
      :type="$route.name == 'app-id' ? 'main' : 'sub'"
    />
    <v-main style="background: #000">
      <Nuxt />
    </v-main>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  },
  mounted() {
    console.log(this.$route.name)
  }
}
</script>
<style>
html {
  overflow-x: hidden;
}
body {
  overflow-x: hidden;
}
</style>