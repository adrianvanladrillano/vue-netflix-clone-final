<template>
  <div>
    {{loadID}}
    <v-card @click="$emit('showDialog', view_id)">
      <v-img
        contain
        style="width: 100%;height: 100%"
        :src="`https://image.tmdb.org/t/p/w200/${poster_path}`"
      ></v-img>
    </v-card>
  </div>
</template>
<script>
import { mapState } from 'vuex'
export default {
  props: ['view_id'],
  data() {
    return {
      poster_path: '',
      id: ''
    }
  },
  computed: {
    ...mapState({
      movies: state => {
        return state.movies
      }
    }),
    loadID() {
      let viewIndex = this.movies.map(el => el.id).indexOf(this.view_id)
      this.poster_path = this.movies[viewIndex].poster_path
      console.log(this.poster_path)
    }
  }
}
</script>