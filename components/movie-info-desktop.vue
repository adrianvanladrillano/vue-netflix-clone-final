<template>
  <div>
    <v-card color="black" dark>
      {{loadID}}
      <div style="position: relative;">
        <netflix-player :video-id="view_id"></netflix-player>

        <div class="px-8" style="position: absolute;bottom: 0px;left: 0px;">
          <v-card color="transparent" style="width: 100%" flat>
            <h1
              style="-webkit-text-stroke: 1px black;"
              class="white--text font-weight-black display-2"
            >{{original_title}}</h1>
            <div class="mt-5">
              <v-btn class="px-10 mr-5" router :to="'/watch/'+ view_id">
                <v-icon left>mdi-play</v-icon>Play
              </v-btn>

              <v-btn @click="onList(view_id)" dark fab small class="mx-1">
                <v-icon>{{added == false ? 'mdi-plus' : 'mdi-minus'}}</v-icon>
              </v-btn>

              <v-btn @click="onDialog()" dark fab small class="mx-1">
                <v-icon>mdi-thumb-up</v-icon>
              </v-btn>

              <v-btn @click="onDialog()" dark fab small class="mx-1">
                <v-icon>mdi-thumb-down</v-icon>
              </v-btn>
            </div>
          </v-card>
        </div>
      </div>

      <v-container class="pa-10">
        <v-row>
          <v-col cols="8">
            <p>
              <span class="mr-2">NEW</span>
              <span class="mr-2">{{release_date}}</span>
              <v-chip outlined small label class="mr-2">{{rated ==false? '13+' : '18+'}}</v-chip>
              <span class="mr-2">2h 16m</span>
              <v-chip outlined small label>HD</v-chip>
            </p>
            <p>{{overview}}</p>
          </v-col>

          <v-col cols="4" style="font-size: .9em">
            <p class="grey--text text--darken-1">
              Cast:
              <span
                class="white--text"
              >Adrian Van Ladrillano, Kenn Yvan Español, CJ Buenaventura, more.</span>
            </p>
            <p class="grey--text text--darken-1">
              Genres:
              <span class="white--text">Superhero, Sci-fi</span>
            </p>
            <p class="grey--text text--darken-1">
              This movie is:
              <span class="white--text">Superhero, Sci-fi</span>
            </p>
          </v-col>
        </v-row>

        <v-row>
          <v-col cols="4" v-for="i in 9" :key="i">
            <netflix-card />
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </div>
</template>
<script>
import { mapState } from 'vuex'

export default {
  props: ['view_id'],
  data() {
    return {
      original_title: '',
      release_date: '',
      rated: '',
      overview: '',
      added: false
    }
  },
  computed: {
    ...mapState({
      movies: state => {
        return state.movies
      },
      list: state => {
        return state.list
      }
    }),
    loadID() {
      let viewIndex = this.movies.map(el => el.id).indexOf(this.view_id)
      this.release_date = this.movies[viewIndex].release_date.substring(0, 4)
      this.original_title = this.movies[viewIndex].original_title
      this.rated = this.movies[viewIndex].adult
      this.overview = this.movies[viewIndex].overview
      this.added =
        this.list.map(el => el).indexOf(this.view_id) == -1 ? false : true
    }
  },
  methods: {
    onList(id) {
      if (this.added == false) {
        this.$store.commit('ADD_TO_LIST', this.view_id)
      } else {
        this.$store.commit('REMOVE_TO_LIST', this.view_id)
      }
    }
  }
}
</script>