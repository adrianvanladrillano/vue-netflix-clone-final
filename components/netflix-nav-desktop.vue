<template>
  <div>
    <v-app-bar
      app
      hide-on-scroll
      v-if="$route.name !='watch-id'"
      flat
      :dark="$route.name !='register' ? true : false"
      :color="$route.name !='register' ? 'transparent' : 'white'"
      class="px-15"
    >
      <v-img
        @click="$router.push('/app/all')"
        class="mr-10"
        contain
        :max-width="$vuetify.breakpoint.mobile ? '20': '100'"
        :src="$vuetify.breakpoint.mobile ? 'https://pngimg.com/uploads/netflix/netflix_PNG15.png': 'https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Netflix_2015_logo.svg/2560px-Netflix_2015_logo.svg.png'"
      ></v-img>

      <v-btn icon v-if="type == 'back'">
        <v-icon color="white">mdi-arrow-left</v-icon>
      </v-btn>
      <v-app-bar-title
        class="white--text font-weight-medium"
        v-if="type == 'sub' || type=='back'"
      >{{title}}</v-app-bar-title>

      <div v-if="$route.name != 'register' && $route.name != 'index' && $route.name != 'login'">
        <v-btn style="text-transform: none" text router to="/app/all">Home</v-btn>
        <v-btn style="text-transform: none" text router to="/app/tv-shows">TV Shows</v-btn>
        <v-btn style="text-transform: none" text router to="/app/movies">Movies</v-btn>
        <v-btn style="text-transform: none" text router to="/my-list">My List</v-btn>
      </div>
      <v-spacer></v-spacer>
      <v-text-field
        hide-details
        v-model="search"
        v-if="search_mode == true"
        @input="$router.push('/search/' + search)"
      ></v-text-field>
      <v-btn
        dark
        icon
        @click="search_mode = true"
        style="text-transform: none"
        v-if="$route.name != 'register' && $route.name != 'index'&& $route.name != 'login'"
      >
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-menu
        offset-y
        color="black"
        v-if="$route.name != 'register' && $route.name != 'index'&& $route.name != 'login'"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-avatar tile width="30" height="30" v-bind="attrs" v-on="on">
            <v-img
              contain
              style="height: 100%"
              src="https://i.pinimg.com/564x/1a/4e/46/1a4e46e64b47fa2925c083c805490b0d.jpg"
            ></v-img>
          </v-avatar>
        </template>
        <v-list dark>
          <v-list-item dense v-for="i in 4" :key="i" class="px-2 my-0 py-0">
            <v-list-item-avatar tile>
              <v-img
                style="border-radius: 4px;max-width: 36px"
                contain
                src="https://upload.wikimedia.org/wikipedia/commons/0/0b/Netflix-avatar.png"
              ></v-img>
            </v-list-item-avatar>
            <v-list-item-title style="font-size: .8em">Username</v-list-item-title>
          </v-list-item>

          <v-list-item dense link router to="/account-settings">
            <v-list-item-title style="font-size: .8em">Account</v-list-item-title>
          </v-list-item>

          <v-list-item dense router to>
            <v-list-item-title style="font-size: .8em">Help Center</v-list-item-title>
          </v-list-item>

          <v-list-item dense link router to="/login">
            <v-list-item-title style="font-size: .8em">Sign out of Netflix</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <template
        v-slot:extension
        v-if="$route.name != 'watch-id' && $route.name != 'register'&& $route.name != 'login'"
      >
        <h1
          class="white--text text-capitalize mr-5 font-weight-regular"
          v-if="$route.name == 'my-list'"
        >My List</h1>
        <h1
          class="white--text text-capitalize mr-5 font-weight-regular"
        >{{$route.params.id == 'tv-shows' ? 'TV Shows' : $route.params.id == 'movies' ? 'Movies' : ''}}</h1>

        <v-btn
          v-if="$route.params.id == 'tv-shows' && $route.params.id == 'movies'"
          dark
          class="text-capitalize font-weight-regular"
          text
          router
          to="/app/movies"
          large
        >Genre</v-btn>
      </template>
      <v-btn
        color="red accent-4"
        class="text-capitalize"
        router
        to="/login"
        v-if="$route.name == 'index'"
      >Sign in</v-btn>
    </v-app-bar>
  </div>
</template>
<script>
export default {
  props: ['type', 'title'],
  data() {
    return {
      search_mode: false,
      search: ''
    }
  }
}
</script>