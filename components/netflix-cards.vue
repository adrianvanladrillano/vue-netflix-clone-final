<template>
  <div>
    <v-sheet elevation="0" width="98vw" color="transparent">
      <div :class="$vuetify.breakpoint.mobile ? '' : 'mx-15'">
        <v-list-item
          class="font-weight-medium white--text px-0"
          dark
          :class="$vuetify.breakpoint.mobile ? 'text-h6' : 'text-h5'"
        >
          {{title}}
          <v-icon color="white">mdi-chevron-right</v-icon>
        </v-list-item>
      </div>
      <v-slide-group class="mt-2" v-if="movies.length == 0">
        <v-slide-item v-for="i in 15" :key="i">
          <v-skeleton-loader
            class="mx-1"
            dark
            :width="$vuetify.breakpoint.mobile ? 100 : 280"
            :height="$vuetify.breakpoint.mobile ? 150 : 500"
            type="card"
          ></v-skeleton-loader>
        </v-slide-item>
      </v-slide-group>
      <v-slide-group class="mt-2" v-else>
        <v-slide-item
          v-for="(movie, index) in randomize(movies)"
          :key="index"
          v-slot="{ active, toggle }"
        >
          <v-card
            class="mx-1 zoom"
            :width="$vuetify.breakpoint.mobile ? 100 : 280"
            :input-value="active"
            active-class="purple white--text"
            @click="toggle;$emit('showDialog', movie.id)"
          >
            <v-img
              :src="!$vuetify.breakpoint.mobile ? `https://image.tmdb.org/t/p/w200/${movie.poster_path}` : `https://image.tmdb.org/t/p/w200/${movie.poster_path}`"
            ></v-img>
          </v-card>
        </v-slide-item>
      </v-slide-group>
    </v-sheet>
  </div>
</template>
<script>
import { mapState } from 'vuex'
export default {
  props: ['title'],
  data() {
    return {}
  },
  methods: {
    randomize(array) {
      return array
        .map(x => [Math.random(), x])
        .sort(([a], [b]) => a - b)
        .map(([_, x]) => x)
    }
  },
  computed: {
    ...mapState({
      movies: state => {
        return state.movies
      }
    })
  }
}
</script>
<style>
.zoom {
  transition: transform 0.2s; /* Animation */
  margin: 0 auto;
}
.zoom:hover {
  z-index: 9;
  transform: scale(1.2);
}
</style>