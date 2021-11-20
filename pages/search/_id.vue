<template>
  <div style="background:black;color: white">
    <netflix-nav type="back" title="My list" />

    <v-container>
      <v-row align="center">
        <v-col cols="6">
          <h1>Search</h1>
          <span class="font-weight-regular grey--text">
            Showing results of:
            <span class="font-weight-medium white--text">{{$route.params.id}}</span>
          </span>
        </v-col>

        <v-col cols="6">
          <span class="font-weight-regular grey--text float-right">
            Showing results of:
            <span class="font-weight-medium white--text">la casa</span>
          </span>
        </v-col>
      </v-row>

      <v-row
        dense
        v-if="filtered_movies.length == 0"
        style="height: 60vh"
        align="center"
        justify="center"
      >
        <v-col>
          <h1>Oh, Darn we don't have that.</h1>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
        </v-col>
      </v-row>

      <v-row dense style="min-height: 60vh">
        <v-col v-for="(movie, index) in filtered_movies" :key="index" cols="4" xl="2">
          <v-card>
            <v-img
              :src="!$vuetify.breakpoint.mobile ? `https://image.tmdb.org/t/p/w200/${movie.poster_path}` : `https://image.tmdb.org/t/p/w200/${movie.poster_path}`"
            ></v-img>
          </v-card>
        </v-col>
      </v-row>
    </v-container>

    <netflix-footer />
  </div>
</template>
<script>
import { mapState } from 'vuex'
export default {
  async fetch({ store }) {
    await store.dispatch('get_netflix')
  },
  data() {
    return {}
  },
  computed: {
    ...mapState({
      movies: state => {
        return state.movies
      }
    }),
    filtered_movies() {
      return this.movies.filter(movie => {
        return (
          !this.$route.params.id ||
          movie.original_title
            .toLowerCase()
            .includes(this.$route.params.id.toLowerCase())
        )
      })
    }
  }
}
</script>