<template>
  <div style="background: #F3F3F3;min-height: 100vh">
    <v-row align="center" justify="center">
      <v-col cols="10" xl="6" lg="6">
        <v-card flat color="transparent">
          <v-row>
            <v-col cols="12" xl="6" lg="6">
              <h1 class="font-weight-regular">
                Account
                <v-chip class="body-1" color="transparent">
                  <v-icon left color="red  darken-2">mdi-movie</v-icon>Member since 2013
                </v-chip>
              </h1>
            </v-col>
          </v-row>

          <v-divider></v-divider>

          <v-row class="py-2">
            <v-col cols="10" xl="3" lg="3">
              <p class="body-1 text-uppercase text--secondary">Membership & Billing</p>
            </v-col>
            <v-col>
              <div>
                <div class="mb-2">
                  <span style="font-size: 1em;" class="font-weight-bold">
                    avpl.dev@gmail.com
                    <a
                      href
                      class="float-right text-decoration-none font-weight-regular"
                    >Change Email</a>
                  </span>
                </div>
                <div class="mb-2">
                  <span style="font-size: 1em;" class="font-weight-regular text--secondary">
                    Password: ********
                    <a
                      href
                      class="float-right text-decoration-none font-weight-regular"
                    >Change Password</a>
                  </span>
                </div>

                <div class="mb-2">
                  <span style="font-size: 1em;" class="font-weight-regular text--secondary">
                    Phone: (995)123-4567
                    <a
                      href
                      class="float-right text-decoration-none font-weight-regular"
                    >Change Phone</a>
                  </span>
                </div>

                <v-divider class="my-5" />

                <div class="mb-2">
                  <span style="font-size: 1em;" class="font-weight-bold text--secondary">
                    <v-icon left>mdi-credit-card-check</v-icon>avpl.dev@gmail.com
                    <a
                      href
                      class="float-right text-decoration-none font-weight-regular"
                    >Manage Payment Info</a>
                  </span>
                </div>

                <v-row no-gutters class="mb-2">
                  <v-col>
                    <span
                      style="font-size: 1em;"
                      class="text--secondary"
                    >Your next billing date is November 23, 2021.</span>
                  </v-col>
                  <v-col cols="4">
                    <a
                      href
                      class="float-right text-decoration-none font-weight-regular"
                    >Add backup payment method</a>
                  </v-col>
                </v-row>
                <div class="text-right mb-2">
                  <a href class="text-decoration-none font-weight-regular">Billing details</a>
                </div>
                <div class="text-right mb-2">
                  <a href class="text-decoration-none font-weight-regular">Change billing day</a>
                </div>
              </div>

              <v-divider class="mb-3"></v-divider>

              <div class="text-right mb-2">
                <a
                  href
                  class="text-decoration-none font-weight-regular"
                >Redeem gift card or promo code</a>
              </div>
              <div class="text-right mb-2">
                <a href class="text-decoration-none font-weight-regular">Where to buy gift cards</a>
              </div>
            </v-col>
          </v-row>

          <v-divider class="mb-5"></v-divider>

          <v-row class="py-2">
            <v-col cols="10" xl="3" lg="3">
              <p class="body-1 text-uppercase text--secondary">PLAN DETAILS</p>
            </v-col>
            <v-col>
              <v-row no-gutters>
                <v-col>
                  <span class="font-weight-medium">Premium</span>
                  <v-chip outlined label>
                    ULTRA
                    <span class="font-weight-medium">HD</span>
                  </v-chip>
                </v-col>
                <v-col cols="3">
                  <a class="float-right">Change plan</a>
                </v-col>
              </v-row>
            </v-col>
          </v-row>

          <v-divider></v-divider>

          <v-row class="py-2">
            <v-col cols="10" xl="3" lg="3">
              <p class="body-1 text-uppercase text--secondary">SETTINGS</p>
            </v-col>
            <v-col>
              <div v-for="i in settings" :key="i" class="mb-1">
                <a>{{i}}</a>
              </div>
            </v-col>
          </v-row>

          <v-divider></v-divider>

          <v-row class="py-2">
            <v-col cols="10" xl="3" lg="3">
              <p class="body-1 text-uppercase text--secondary">PROFILE & PARENTAL CONTROLS</p>
            </v-col>
            <v-col>
              <v-list-item two-line v-for="i in 5" :key="i">
                <v-list-item-avatar tile size="56">
                  <v-img
                    contain
                    src="https://occ-0-5540-64.1.nflxso.net/dnm/api/v6/K6hjPJd6cR6FpVELC5Pd6ovHRSk/AAAABW91hUV-HH6GcMZh8tmyG0092xvVo4TbKUai2Ju0x5mIB-oYki4BR0dm3ePE2ZUeylyCfUxVso2Re9qdcUYoC5mfZw.png?r=c71"
                  ></v-img>
                </v-list-item-avatar>

                <v-list-item-content>
                  <v-list-item-title class="font-weight-bold">Username</v-list-item-title>
                  <v-list-item-subtitle>All Maturity Ratings</v-list-item-subtitle>
                </v-list-item-content>

                <v-list-item-actions>
                  <v-btn icon>
                    <v-icon>mdi-chevron-down</v-icon>
                  </v-btn>
                </v-list-item-actions>
              </v-list-item>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      settings: [
        'Test participation',
        'Manage download devices',
        'Activate a device',
        'Recent device streaming activity',
        'Sign out of all devices',
        'Download your personal information'
      ]
    }
  }
}
</script>