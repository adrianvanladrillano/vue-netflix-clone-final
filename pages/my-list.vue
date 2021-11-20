<template>
  <div style="background:black;color: white">
    <!-- <p>{{ list}}</p> -->
    <v-container>
      <v-row align="center" justify="center" v-if="list.length == 0" style="min-height: 85vh">
        <v-col cols="6">
          <h1>You havent added anything on your list.</h1>
          <p
            class="grey--text darken-3"
          >Lorem ipsum, dolor sit amet consectetur adipisicing elit. Reiciendis delectus, repellat quia odio soluta natus eaque animi magnam officia non explicabo enim eos qui fugit quibusdam praesentium vitae aperiam suscipit.</p>
        </v-col>
      </v-row>
      <v-row dense>
        <v-col v-for="item in list" :key="item" cols="4" xl="2">
          <netflix-vertical @showDialog="showDialog" :view_id="item" />
        </v-col>
      </v-row>
    </v-container>

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
import { mapState } from 'vuex'
export default {
  async fetch({ store }) {
    await store.dispatch('get_netflix')
  },
  data() {
    return {
      viewIndex: 0
    }
  },
  computed: {
    ...mapState({
      list: state => {
        return state.list
      },
      movies: state => {
        return state.movies
      }
    })
  },
  methods: {
    showDialog(id) {
      let index = this.movies.map(el => el.id).indexOf(id)
      this.dialogView = true
      this.viewIndex = index
    }
  }
}
</script>