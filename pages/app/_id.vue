<template>
  <div style="color: white">
    <!-- Navigation -->
    <!-- <netflix-nav type="main" /> -->

    <!-- Main Container  -->
    <v-row style="margin-top: -117px">
      <v-col>
        <!-- Desktop Hero -->
        <div style="position: relative;z-index: 0">
          <iframe
            v-if="!$vuetify.breakpoint.mobile"
            style="width: 100%;height: 100vh;margin-top: -80px"
            src="https://www.youtube.com/embed/6ZfuNTqbHE8?autoplay=1&mute=1&controls=0"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
          <div class="px-8" style="position: absolute;bottom: 230px;left: 40px;">
            <v-card color="transparent" style="width: 25vw" flat>
              <v-img
                src="https://terrigen-cdn-dev.marvel.com/content/prod/1x/avengersinfinitywar_lob_log_03.png"
              ></v-img>
              <v-row class="mt-5">
                <v-col cols="4">
                  <v-btn x-large block class="text-capitalize">
                    <v-icon large left class="pr-5">mdi-play</v-icon>Play
                  </v-btn>
                </v-col>

                <v-col cols="5">
                  <v-btn x-large block class="text-capitalize" dark @click="onDialog()">
                    <v-icon large left class="pr-5">mdi-information-outline</v-icon>More Info
                  </v-btn>
                </v-col>
              </v-row>
            </v-card>
          </div>
        </div>

        <!-- Mobile Hero -->
        <v-row v-if="$vuetify.breakpoint.mobile">
          <v-col>
            <v-img
              style="height: 60vh;"
              src="https://cdn.wallpapersafari.com/2/30/S1OntZ.jpg"
              gradient="to bottom, rgba(0,0,0,.99), rgba(0,0,0,0), rgba(0,0,0,.99)"
            ></v-img>

            <v-card dark style="margin-top: -150px" color="transparent" align="center">
              <v-img
                width="60vw"
                src="https://terrigen-cdn-dev.marvel.com/content/prod/1x/avengersinfinitywar_lob_log_03.png"
              ></v-img>
              <v-row justify="center" align="center">
                <v-col cols="4" align="center" justify="center">
                  <v-btn icon router to="/my-list">
                    <v-icon color="white">mdi-plus</v-icon>
                  </v-btn>
                  <p style="font-size: .6em;">My List</p>
                </v-col>
                <v-col cols="4">
                  <v-btn color="white" class="black--text text-capitalize" router to="/watch/id">
                    <v-icon left>mdi-play</v-icon>Play
                  </v-btn>
                </v-col>
                <v-col cols="4">
                  <v-btn icon @click="dialogView = true">
                    <v-icon color="white">mdi-information-outline</v-icon>
                  </v-btn>
                  <p style="font-size: .6em;">More Info</p>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>

        <!-- Main Container -->
        <v-container :class="$vuetify.breakpoint.mobile ? 'mx-0 mt-5' : 'mx-0'">
          <netflix-cards
            @showDialog="showDialog"
            title="Popular on Netflix"
            :style="$vuetify.breakpoint.mobile ? '' : 'margin-top: -180px;z-index: 999'"
          />

          <netflix-top @showDialog="showDialog" class="mt-10" />

          <netflix-cards @showDialog="showDialog" title="Trending Now" class="mt-10" />

          <netflix-cards
            class="mt-15"
            @showDialog="showDialog"
            title="Continue watching for Username"
          />

          <netflix-cards
            @showDialog="showDialog"
            title="US TV Shows"
            style="z-index: 99"
            class="mt-10"
          />

          <netflix-cards @showDialog="showDialog" title="Something" class="mt-10" />

          <netflix-cards @showDialog="showDialog" title="Something" class="mt-10" />
        </v-container>
      </v-col>
    </v-row>

    <!-- More info mobile -->
    <v-bottom-sheet
      style="z-index: 99999"
      app
      v-model="dialogView"
      v-if="movies.length != 0 && $vuetify.breakpoint.mobile"
    >
      <v-card color="black" dark class="px-4 py-4">
        <v-row dense>
          <v-col cols="4">
            <v-img
              contain
              style="width: 100%;height: 100%"
              :src="!$vuetify.breakpoint.mobile ? `https://image.tmdb.org/t/p/w200/${movies[viewIndex].poster_path}` : `https://image.tmdb.org/t/p/w200/${movies[viewIndex].poster_path}`"
            ></v-img>
          </v-col>
          <v-col cols="8">
            <v-list-item two-line class="px-0">
              <v-list-item-content>
                <v-list-item-title
                  class="font-weight-bold text-wrap"
                >{{movies[viewIndex].original_title}}</v-list-item-title>
                <v-list-item-subtitle style="font-size: .7em">
                  <span class="mr-2">{{movies[viewIndex].release_date.substring(0,4)}}</span>
                  <span class="mr-2">
                    <v-chip
                      x-small
                      label
                      outlined
                    >{{movies[viewIndex].adult == false? '13+' : '18+'}}</v-chip>
                  </span>
                  <span>3 Seasons</span>
                </v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-action>
                <v-btn fab x-small @click="dialogView = false">
                  <v-icon>mdi-close</v-icon>
                </v-btn>
              </v-list-item-action>
            </v-list-item>

            <p style="font-size: .7em">{{movies[viewIndex].overview}}</p>
          </v-col>
        </v-row>

        <v-row align="center" justify="center" no-gutters>
          <v-col>
            <v-btn block light router :to="'/watch/'+ movies[viewIndex].id">
              <v-icon left>mdi-play</v-icon>Play
            </v-btn>
          </v-col>

          <v-col cols="3" align="center">
            <v-btn icon @click="dialogView = true">
              <v-icon color="white">mdi-download</v-icon>
            </v-btn>
            <p style="font-size: .5em;">Download</p>
          </v-col>

          <v-col cols="3" align="center">
            <v-btn icon @click="dialogView = true">
              <v-icon color="white">mdi-play</v-icon>
            </v-btn>
            <p style="font-size: .5em;">Preview</p>
          </v-col>
        </v-row>

        <v-row no-gutters>
          <v-col>
            <v-list-item class="px-0" link router to="/watch">
              <v-list-item-avatar>
                <v-icon color="white">mdi-information-outline</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title class="body-2 font-weight-regular">Episodes & Info</v-list-item-title>
              </v-list-item-content>

              <v-list-item-action>
                <v-btn fab x-small @click="dialogView = false">
                  <v-icon>mdi-arrow-right</v-icon>
                </v-btn>
              </v-list-item-action>
            </v-list-item>
          </v-col>
        </v-row>
      </v-card>
    </v-bottom-sheet>

    <!-- More info desktop -->
    <v-dialog
      v-model="dialogView"
      width="1000"
      v-if="movies.length != 0 && !$vuetify.breakpoint.mobile"
    >
      <movie-info-desktop :view_id="movies[viewIndex].id" />
    </v-dialog>

    <netflix-footer />
  </div>
</template>
<script>
import axios from 'axios'
import { mapState } from 'vuex'
import { Youtube } from 'vue-youtube'

export default {
  async fetch({ store }) {
    await store.dispatch('get_netflix')
  },

  data() {
    return {
      dialogView: false,
      viewIndex: 0
    }
  },
  computed: {
    ...mapState({
      movies: state => {
        return state.movies
      }
    })
  },
  mounted() {},
  methods: {
    onDialog() {
      this.dialogView = true
    },
    showDialog(id) {
      let index = this.movies.map(el => el.id).indexOf(id)
      this.dialogView = true
      this.viewIndex = index
    }
  }
}
</script>
<style>
.v-sheet {
  background: black;
}
.image-container {
  position: relative;
  width: 200px;
  height: 300px;
}
.image-container .after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: none;
  color: #fff;
}
.image-container:hover .after {
  display: block;
  background: rgba(0, 0, 0, 0.6);
}
</style>