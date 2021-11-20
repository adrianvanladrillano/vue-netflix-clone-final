<template>
  <div>
    <div
      style="background-image: linear-gradient(rgb(0, 0, 0, 0.5),rgb(0, 0, 0, 0.5)), url('https://assets.nflxext.com/ffe/siteui/vlv3/b8e09d9c-d1e7-4800-afd9-810e41ace684/76604e6d-7996-4834-bda0-bbae48357f02/PH-en-20210607-popsignuptwoweeks-perspective_alpha_website_large.jpg');width: 100vw;"
    >
      <v-row align="center" justify="center" style="min-height: 60vh">
        <v-col cols="5">
          <v-card dark color="transparent" flat class="text-center">
            <h1 class="display-3 font-weight-bold">
              Unlimited movies, TV
              <br />shows, and more.
            </h1>
            <h2 class="font-weight-regular">Watch anywhere. Cancel anytime.</h2>

            <h3
              class="font-weight-regular mt-5"
            >Ready to watch? Enter your email to create or restart your membership.</h3>

            <v-row no-gutters justify="center">
              <v-col cols="8">
                <v-btn
                  block
                  color="red accent-4"
                  x-large
                  class="mt-5"
                  router
                  to="/register"
                >Get Started</v-btn>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </div>

    <v-row align="center" justify="center">
      <v-col cols="7">
        <v-row no-gutters align="center" class="py-10">
          <v-col cols="12" xl="6" lg="6">
            <v-card dark color="transparent">
              <h1 class="display-2 font-weight-medium">Enjoy on your TV.</h1>
              <h2
                class="font-weight-regular mt-2"
              >Watch on Smart TVs, Playstation, Xbox, Chromecast, Apple TV, Blu-ray players, and more.</h2>
            </v-card>
          </v-col>

          <v-col cols="12" xl="6" lg="6">
            <v-img
              style="width: 100%"
              contain
              src="https://assets.nflxext.com/ffe/siteui/acquisition/ourStory/fuji/desktop/tv.png"
            ></v-img>
          </v-col>
        </v-row>

        <v-row no-gutters align="center" class="py-10">
          <v-col cols="12" xl="6" lg="6">
            <v-img
              style="width: 100%"
              contain
              src="https://assets.nflxext.com/ffe/siteui/acquisition/ourStory/fuji/desktop/mobile-0819.jpg"
            ></v-img>
          </v-col>
          <v-col cols="12" xl="6" lg="6">
            <v-card dark color="transparent">
              <h1 class="display-2 font-weight-medium">Download your shows to watch offline.</h1>
              <h2
                class="font-weight-regular mt-2"
              >Save your favorites easily and always have something to watch.</h2>
            </v-card>
          </v-col>
        </v-row>

        <v-row no-gutters align="center" class="py-10">
          <v-col cols="12" xl="6" lg="6">
            <v-card dark color="transparent">
              <h1 class="display-2 font-weight-medium">Watch everywhere.</h1>
              <h2
                class="font-weight-regular mt-2"
              >Stream unlimited movies and TV shows on your phone, tablet, laptop, and TV.</h2>
            </v-card>
          </v-col>

          <v-col cols="12" xl="6" lg="6">
            <v-img
              style="width: 100%"
              contain
              src="https://assets.nflxext.com/ffe/siteui/acquisition/ourStory/fuji/desktop/tv.png"
            ></v-img>
          </v-col>
        </v-row>

        <v-row no-gutters align="center" class="py-10">
          <v-col cols="12" xl="6" lg="6">
            <v-img
              style="width: 100%"
              contain
              src="https://occ-0-5540-64.1.nflxso.net/dnm/api/v6/19OhWN2dO19C9txTON9tvTFtefw/AAAABdFTpLmANuJpYneLq8L5m7CunMCi8e8Nl4y7xaPVWzG3IeoDoq17egTQAthApKg_4sdRWdwuR8KadWu1frjL3JQImpwq.png?r=fcd"
            ></v-img>
          </v-col>
          <v-col cols="12" xl="6" lg="6">
            <v-card dark color="transparent">
              <h1 class="display-2 font-weight-medium">Create profiles for kids.</h1>
              <h2
                class="font-weight-regular mt-2"
              >Send kids on adventures with their favorite characters in a space made just for them—free with your membership.</h2>
            </v-card>
          </v-col>
        </v-row>

        <v-row no-gutters align="center" justify="center" class="py-10">
          <v-col cols="8">
            <v-card dark color="transparent" class="text-center">
              <h1 class="display-2 font-weight-medium">Frequently Asked Questions</h1>
            </v-card>

            <v-card>Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam ullam unde suscipit eius tenetur fugiat nulla non neque iusto ex tempora, earum exercitationem accusantium dolor libero natus. Sapiente, nihil voluptatem.</v-card>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </div>
</template>
<script>
export default {
  async fetch({ store }) {
    await store.dispatch('get_netflix')
  },
  data() {
    return {}
  }
}
</script>