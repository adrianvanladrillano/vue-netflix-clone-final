<template>
  <div style="z-index: 999">
    <v-sheet elevation="8" width="98vw" color="transparent" style="z-index: 999">
      <div :class="$vuetify.breakpoint.mobile ? '' : 'mx-15'">
        <a
          :class="$vuetify.breakpoint.mobile ? 'text-h6' : 'text-h5'"
          class="font-weight-medium white--text"
          style="z-index:9999"
        >Top 10 in the Philippines Today</a>
      </div>
      <v-slide-group class="mt-2">
        <v-slide-item v-for="n in 10" :key="n" v-slot="{ active, toggle }">
          <div style="position: relative">
            <v-card
              class="mx-1"
              :width="$vuetify.breakpoint.mobile ? 150 : 280"
              :input-value="active"
              @click="toggle"
              flat
              color="transparent"
            >
              <v-row no-gutters>
                <v-col cols="6">
                  <v-img
                    src="http://pngimg.com/uploads/number1/small/number1_PNG14893.png"
                    style="filter: invert(.1);height: 100%"
                  ></v-img>
                </v-col>
                <v-col cols="6">
                  <v-img
                    style="margin-left: -20px"
                    src="https://i.pinimg.com/originals/42/8f/1c/428f1c6eb0e1c8ff7889d6f7b147ed15.jpg"
                  ></v-img>
                </v-col>
              </v-row>
            </v-card>
          </div>
        </v-slide-item>
      </v-slide-group>
    </v-sheet>
  </div>
</template>
<script>
export default {
  data() {
    return {}
  }
}
</script>