<template>
  <div>
    <v-bottom-navigation
      app
      v-if="$vuetify.breakpoint.mobile"
      background-color="#000"
      grow
      v-model="value"
      style="z-index: 999;font-weight: 500;font-size: .7em"
      dark
    >
      <v-btn value="recent" style="font-weight: 400;font-size: .8em" router to="/app">
        <span>Home</span>
        <v-icon>mdi-home</v-icon>
      </v-btn>

      <v-btn value="recent" style="font-weight: 400;font-size: .8em" router to="/watch/1">
        <span>Play Something</span>
        <v-icon>mdi-shuffle-variant</v-icon>
      </v-btn>

      <v-btn value="recent" style="font-weight: 400;font-size: .8em" router to="/coming-soon">
        <span>Coming Soon</span>
        <v-icon>mdi-filmstrip-box-multiple</v-icon>
      </v-btn>

      <v-btn value="recent" style="font-weight: 400;font-size: .8em" router to="/downloads">
        <span>Downloads</span>
        <v-icon>mdi-download-circle-outline</v-icon>
      </v-btn>
    </v-bottom-navigation>
    <v-footer
      dark
      v-if="!$vuetify.breakpoint.mobile"
      justify="center"
      class="py-15"
      style="background: #000"
    >
      <v-row align="center" justify="center" style="font-size: .8em">
        <v-col cols="6">
          <v-row>
            <v-col>
              <v-icon large class="mr-4" color="grey darken-2">mdi-facebook</v-icon>
              <v-icon large class="mr-4" color="grey darken-2">mdi-instagram</v-icon>
              <v-icon large class="mr-4" color="grey darken-2">mdi-twitter</v-icon>
              <v-icon large class="mr-4" color="grey darken-2">mdi-youtube</v-icon>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="3" v-for="i in items" :key="i">
              <div>
                <a class="grey--text lighten-2">{{i}}</a>
              </div>
            </v-col>
          </v-row>

          <v-row>
            <v-col>
              <v-chip outlined label color="grey ">Service code</v-chip>

              <p class="grey--text lighten-2 mt-3">© 1997-2021 Netflix, Inc.</p>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-footer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      items: [
        'Audio and Subtitles',
        'Audio Description',
        'Help Center',
        'Gift Cards',
        'Media Center',
        'Investor Relations',
        'Jobs',
        'Terms of Use',
        'Privacy',
        'Legal Notices',
        'Cookie Preference',
        'Corporate Information',
        'Contact Us'
      ]
    }
  }
}
</script>