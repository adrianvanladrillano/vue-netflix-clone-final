<template>
  <div style="background:black;color: white">
    <v-app-bar dense app color="transparent" flat class="mx-10 mt-5">
      <v-btn icon dark @click="$router.go(-1)">
        <v-icon large>mdi-arrow-left</v-icon>
      </v-btn>
    </v-app-bar>
    <netflix-player :video-id="$route.params.id"></netflix-player>

    <v-bottom-sheet v-model="controls" hide-overlay>
      <v-card color="transparent" dark class="mx-10 mb-5 d-flex" flat>
        <v-btn icon dark @click="playVideo" class="mr-5">
          <v-icon large>mdi-pause</v-icon>
        </v-btn>

        <h2>
          Ragnarok:
          <span class="font-weight-regular grey--text lighten-2">Episode: 1</span>
        </h2>

        <v-spacer></v-spacer>

        <v-btn icon dark @click="playVideo" class="mx-5">
          <v-icon large>mdi-play</v-icon>
        </v-btn>

        <v-btn icon dark @click="playVideo" class="mx-5">
          <v-icon large>mdi-box</v-icon>
        </v-btn>

        <v-btn icon dark @click="playVideo" class="mx-5">
          <v-icon large>mdi-fullscreen</v-icon>
        </v-btn>

        <v-btn icon dark @click="playVideo">
          <v-icon large>mdi-pause</v-icon>
        </v-btn>
      </v-card>
    </v-bottom-sheet>
  </div>
</template>
<script>
export default {
  data() {
    return {
      controls: true
    }
  },
  mounted() {}
}
</script>
