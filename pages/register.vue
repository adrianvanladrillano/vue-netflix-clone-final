<template>
  <div style="height: 100vh;background: #fff">
    <v-row style="height: 80vh" align="center">
      <v-col class="pt-10" align="center">
        <v-card max-width="350" flat v-if="step == 1">
          <v-card-title class="text-center text-h6 font-weight-regular d-flex flex-column">
            <v-img src="/step1.jpg"></v-img>
            <span class="caption text-uppercase mt-5">
              Step
              <span class="font-weight-bold">1</span> of
              <span class="font-weight-bold">3</span>
            </span>
            <h2>Finish setting up your account</h2>
            <p
              class="body-2 mt-5"
            >Netflix is personalized for you. Create a password to watch on any device at any time.</p>
          </v-card-title>

          <v-btn dark block color="red accent-3" large @click="step++">Next</v-btn>
        </v-card>

        <v-card class="mx-auto" max-width="400" flat v-if="step == 2">
          <v-card-title class="text-h6 font-weight-regular d-flex">
            <span class="caption text-uppercase mt-5">
              Step
              <span class="font-weight-bold">1</span> of
              <span class="font-weight-bold">3</span>
            </span>
            <h2>Create a password to start your membership</h2>
            <p class="body-2 mt-5">
              Just a few more steps and you're done!
              We hate paperwork, too.
            </p>
          </v-card-title>

          <v-card-text>
            <v-text-field outlined label="Email" v-model="email"></v-text-field>
            <v-text-field outlined label="Add a password" type="password" v-model="password"></v-text-field>
            <v-checkbox class="py-0 my-0" label="Please do not email me netflix offers."></v-checkbox>
          </v-card-text>

          <v-card-actions>
            <v-btn
              class="white--text"
              block
              color="red"
              large
              @click="step++"
              :disabled="password == ''  ? true : email == ''  ? true : false"
            >Next</v-btn>
          </v-card-actions>
        </v-card>

        <v-card class="mx-auto" max-width="350" flat v-if="step == 3">
          <v-card-title class="text-center text-h6 font-weight-regular d-flex flex-column">
            <v-icon x-large color="red">mdi-check-circle-outline</v-icon>
            <span class="caption text-uppercase mt-5">
              Step
              <span class="font-weight-bold">2</span> of
              <span class="font-weight-bold">3</span>
            </span>
            <h2>Choose your plan.</h2>
          </v-card-title>

          <v-card-text class="text-left">
            <div class="d-flex">
              <v-icon color="red" class="mr-2">mdi-check</v-icon>
              <p class="body-2 mt-5">No commitments, cancel anytime.</p>
            </div>

            <div class="d-flex">
              <v-icon color="red" class="mr-2">mdi-check</v-icon>
              <p class="body-2 mt-5">Everything on Netflix for one low price.</p>
            </div>

            <div class="d-flex">
              <v-icon color="red" class="mr-2">mdi-check</v-icon>
              <p class="body-2 mt-5">No ads and no extra fees. Ever.</p>
            </div>
          </v-card-text>

          <v-btn dark block color="red accent-3" large @click="step++">Next</v-btn>
        </v-card>

        <v-card class="mx-auto" max-width="820" flat v-if="step == 4">
          <v-card-text class="text-left">
            <span class="caption text-uppercase mt-5">
              Step
              <span class="font-weight-bold">2</span> of
              <span class="font-weight-bold">3</span>
            </span>
            <h1 class="text--primary">Choose the plan that’s right for you</h1>
            <div class="d-flex flex-column mt-4">
              <span class="body-2">
                <v-icon left color="red">mdi-check</v-icon>No commitments, cancel anytime.
              </span>
              <span class="body-2">
                <v-icon left color="red">mdi-check</v-icon>Everything on Netflix for one low price.
              </span>

              <span class="body-2">
                <v-icon left color="red">mdi-check</v-icon>No ads and no extra fees. Ever.
              </span>
            </div>
          </v-card-text>
          <v-row class="px-5 mb-4" dense>
            <v-col cols="4" v-if="!$vuetify.breakpoint.mobile"></v-col>

            <v-col cols="3" xl="2" v-for="plan in plans" :key="plan">
              <v-card
                flat
                class="px-0 py-5"
                :color="chosen_plan == plan.plan_name ? 'red' : 'red lighten-2'"
                :outlined="chosen_plan == plan.plan_name ? false : true"
                align="center"
                justify="center"
                @click="chosen_plan = plan.plan_name"
              >
                <span class="white--text font-weight-medium body-small">{{plan.plan_name}}</span>
              </v-card>
            </v-col>
          </v-row>
          <div class="px-5">
            <v-row class="mt-2" v-if="$vuetify.breakpoint.mobile">
              <v-col class="text-center">
                <span class="text--secondary body-regular font-weight-regular">Monthly Price</span>
              </v-col>
            </v-row>

            <!-- Monthly Price -->
            <v-row dense>
              <v-col cols="4" class="text-left" v-if="!$vuetify.breakpoint.mobile">
                <span class="text--secondary body-regular">Monthly price</span>
              </v-col>

              <v-col v-for="plan in plans" :key="plan" class="text-center">
                <span
                  class="body-regular"
                  :class="chosen_plan == plan.plan_name ? 'red--text font-weight-bold' : 'text--secondary'"
                >₱{{plan.plan_price}}</span>
              </v-col>
            </v-row>

            <v-divider class="my-4"></v-divider>

            <v-row v-if="$vuetify.breakpoint.mobile">
              <v-col class="text-center">
                <span class="text--secondary body-regular font-weight-regular">Video Quality</span>
              </v-col>
            </v-row>

            <!-- Video quality -->
            <v-row dense>
              <v-col cols="4" class="text-left" v-if="!$vuetify.breakpoint.mobile">
                <span class="text--secondary justify-space-around body-regular">Video Quality</span>
              </v-col>

              <v-col v-for="plan in plans" :key="plan" class="text-center">
                <span
                  class="body-regular"
                  :class="chosen_plan == plan.plan_name ? 'red--text font-weight-bold' : 'text--secondary'"
                >{{plan.plan_quality}}</span>
              </v-col>
            </v-row>

            <v-divider class="my-4"></v-divider>

            <v-row v-if="$vuetify.breakpoint.mobile">
              <v-col class="text-center">
                <span class="text--secondary body-regular font-weight-regular">Resolution</span>
              </v-col>
            </v-row>

            <!-- Monthly Price -->
            <v-row dense>
              <v-col cols="4" class="text-left" v-if="!$vuetify.breakpoint.mobile">
                <span class="text--secondary body-regular">Resolution</span>
              </v-col>

              <v-col v-for="plan in plans" :key="plan" class="text-center">
                <span
                  class="body-regular"
                  :class="chosen_plan == plan.plan_name ? 'red--text font-weight-bold' : 'text--secondary'"
                >{{plan.plan_resolution}}</span>
              </v-col>
            </v-row>

            <v-divider class="my-4"></v-divider>

            <v-row v-if="$vuetify.breakpoint.mobile">
              <v-col class="text-center">
                <span
                  class="text--secondary body-regular font-weight-regular"
                >Devices you can use to watch</span>
              </v-col>
            </v-row>

            <!-- Devices -->
            <v-row dense class="mt-4">
              <v-col cols="4" class="text-left" v-if="!$vuetify.breakpoint.mobile">
                <span class="text--secondary body-regular">Devices you can use to watch</span>
              </v-col>

              <v-col v-for="plan in plans" :key="plan" class="text-center">
                <div class="d-flex flex-column">
                  <div
                    class="mb-5 d-flex flex-column"
                    v-for="device in plan.plan_devices"
                    :key="device"
                  >
                    <v-icon
                      :color="chosen_plan == plan.plan_name ? 'red' : 'text--secondary'"
                    >mdi-{{device == 'computer' ? 'laptop' : device == 'computer' ? 'laptop' : device}}</v-icon>
                    <span
                      class="text-capitalize body-small"
                      :class="chosen_plan == plan.plan_name ? 'red--text font-weight-bold' : 'text--secondary'"
                    >{{device}}</span>
                  </div>
                </div>
              </v-col>
            </v-row>
          </div>

          <v-card-text class="body-small">
            HD (720p), Full HD (1080p), Ultra HD (4K) and HDR availability subject to your internet service and device capabilities. Not all content is available in all resolutions. See our Terms of Use for more details.
            <br />
            <br />Only people who live with you may use your account. Watch on 4 different devices at the same time with Premium, 2 with Standard, and 1 with Basic and Mobile.
          </v-card-text>
          <v-card-actions>
            <v-btn
              class="white--text"
              block
              color="red accent-3"
              large
              @click="step++"
              :disabled="chosen_plan == ''"
            >Next</v-btn>
          </v-card-actions>
        </v-card>

        <v-card class="mx-auto" max-width="480" flat v-if="step == 5">
          <v-card-title class="text-center text-h6 font-weight-regular d-flex flex-column">
            <v-icon x-large color="red">mdi-lock-reset</v-icon>
            <span class="caption text-uppercase mt-5">
              Step
              <span class="font-weight-bold">3</span> of
              <span class="font-weight-bold">3</span>
            </span>
            <h2>Set up your payment</h2>
          </v-card-title>

          <v-card-text class="text-center px-15">
            <p class="body-2 mt-5">Your membership starts as soon as you set up payment.</p>

            <div class="d-flex justify-space-around">
              <v-icon color="red">mdi-check</v-icon>
              <p class="body-2 mt-5">No commitments.</p>

              <v-icon color="red">mdi-check</v-icon>
              <p class="body-2 mt-5">Cancel online anytime.</p>
            </div>
          </v-card-text>

          <v-card outlined class="my-2 py-1 mx-5" v-for="payment in payments" :key="payment" @click>
            <v-list-item>
              <v-list-item-icon>
                <v-icon>mdi-{{payment.icon}}</v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title class="body-regular">{{payment.title}}</v-list-item-title>
              </v-list-item-content>

              <v-list-item-action>
                <v-icon>mdi-chevron-right</v-icon>
              </v-list-item-action>
            </v-list-item>
          </v-card>

          <v-card-actions>
            <v-btn dark block color="red accent-3" class="px-5" large @click="step++">Next</v-btn>
          </v-card-actions>
        </v-card>

        <v-card class="mx-auto" max-width="480" flat v-if="step == 6">
          <v-card-title class="text-center text-h6 font-weight-regular d-flex flex-column">
            <v-icon x-large color="red">mdi-check</v-icon>
            <span class="caption text-uppercase mt-5">
              Step
              <span class="font-weight-bold">3</span> of
              <span class="font-weight-bold">3</span>
            </span>
            <h2>Registration Complete</h2>
          </v-card-title>

          <v-card-text class="text-center px-15">
            <p class="body-2 mt-5">
              Account created sucessfully! Your first billing will start on
              <span
                class="font-weight-black text--primary"
              >{{today}}</span>
            </p>

            <p>Thank you for subscribing</p>
          </v-card-text>

          <v-card-actions>
            <v-btn dark block color="red accent-3" class="px-5" large router to="/login">LOGIN</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <v-footer absolute background-color="#F3F3F3">
      <v-card
        height="20vh"
        color="transparent"
        flat
      >Lorem ipsum dolor sit amet consectetur, adipisicing elit. Facilis dignissimos ab iusto iste, quo debitis omnis saepe itaque repellendus, eligendi dolores placeat nostrum sed dolor voluptatibus! Nemo ipsam voluptatum voluptatem.</v-card>
    </v-footer>
  </div>
</template>
<script>
import moment from 'moment'
export default {
  data() {
    return {
      today: moment()
        .add(30, 'days')
        .format('MMMM Do YYYY'),
      step: 1,
      email: '',
      password: '',
      chosen_plan: '',
      payments: [
        {
          title: 'Credit Card or Debit Card',
          icon: 'credit-card-outline'
        },
        {
          title: 'Digital Wallet',
          icon: 'wallet-outline'
        },
        {
          title: 'Postpaid Mobile Bill',
          icon: 'cash-multiple'
        },
        {
          title: 'Gift Code',
          icon: 'wallet-giftcard'
        }
      ],
      plans: [
        {
          plan_name: 'Mobile',
          plan_price: '149',
          plan_quality: 'Good',
          plan_resolution: '480p',
          plan_devices: ['cellphone', 'tablet']
        },
        {
          plan_name: 'Basic',
          plan_price: '369',
          plan_quality: 'Good',
          plan_resolution: '480p',
          plan_devices: ['cellphone', 'tablet', 'computer', 'television']
        },
        {
          plan_name: 'Standard',
          plan_price: '459',
          plan_quality: 'Better',
          plan_resolution: '1080p',
          plan_devices: ['cellphone', 'tablet', 'computer', 'television']
        },
        {
          plan_name: 'Premium',
          plan_price: '549',
          plan_quality: 'Best',
          plan_resolution: '4K+HDR',
          plan_devices: ['cellphone', 'tablet', 'computer', 'television']
        }
      ]
    }
  },
  computed: {},
  methods: {}
}
</script>
<style>
.body-small {
  font-size: 0.8em;
}
.body-regular {
  font-size: 0.9em;
}
</style>