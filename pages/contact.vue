<template>
  <v-container
    class="d-flex align-center"
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%' : ''"
  >
    <v-row>
      <v-col
        md="6"
        sm="6"
        class="d-flex flex-column justify-center"
      >
        <h1
          :class="$vuetify.breakpoint.xs ? 'mx-auto' : ''"
        >
          Contact me
        </h1>

        <h4
          :class="$vuetify.breakpoint.xs ? 'mx-auto' : ''"
        >
          Let's get in touch! 🤟
        </h4>

        <v-card
          flat
          :class="$vuetify.breakpoint.xs ? 'd-flex align-center mb-3 py-4 px-2' : 'd-flex align-center mb-5 py-4 px-2'"
          v-for="(card, i) in cards"
          :key="i"
          :outlined="!$vuetify.theme.dark"
          :style="$vuetify.breakpoint.xs ? 'width: 100%;' : 'width: 18rem;'"
        >
          <img
            :src="card.icon"
            class="mx-3"
            height="24"
            width="24"
          >

          <v-card-text
            class="pa-0"
            ref="textToCopy"
          >
            {{ card.text }}
          </v-card-text>

          <v-btn
            icon
            color="grey"
            @click="copyText(card.text)"
          >
            <v-icon>
              mdi-content-copy
            </v-icon>
          </v-btn>
        </v-card>
      </v-col>

      <v-col
        md="6"
        sm="6"
      >
        <v-card
          :class="$vuetify.breakpoint.xs ? 'pa-1' : 'pa-10 '"
        >
          <v-form
            v-model="valid"
          >
            <v-card-title
              :style="$vuetify.breakpoint.xs ? '' : 'font-size: 30px;'"
              class="mb-10 py-0"
              :class="$vuetify.breakpoint.xs ? 'mb-10 pt-4' : 'mb-10 py-0'"
            >
              <span
                :class="$vuetify.breakpoint.xs ? 'mx-auto' : ''"
              >
                Send me a message 🚀
              </span>
            </v-card-title>

            <v-card-text
              class="pt-0"
            >
              <v-text-field
                filled
                rounded
                clearable
                required
                clear-icon="mdi-window-close"
                label="Name"
                v-model="name"
                hide-details="auto"
                class="rounded"
                :color="$vuetify.theme.dark ? 'white' : 'indigo'"
                :rules="nameRules"
              >
              </v-text-field>
            </v-card-text>
            
            <v-card-text
              class="pt-0"
            >
              <v-text-field
                filled
                rounded
                auto-grow
                clearable
                required
                clear-icon="mdi-window-close"
                label="Email"
                v-model="email"
                placeholder="example@gmail.com"
                hide-details="auto"
                class="rounded"
                :color="$vuetify.theme.dark ? 'white' : 'indigo'"
                :rules="emailRules"
              >
              </v-text-field>
            </v-card-text>

            <v-card-text
              class="pt-0"
            >
              <v-textarea
                filled
                rounded
                auto-grow
                counter
                clearable
                required
                clear-icon="mdi-window-close"
                maxlength="500"
                label="Message"
                v-model="message"
                class="rounded"
                :color="$vuetify.theme.dark ? 'white' : 'indigo'"
                :rules="messageRules"
              ></v-textarea>
            </v-card-text>

            <v-card-text
              class="pt-0"
            >
              <v-btn
                x-large
                color="indigo"
                elevation="0"
                style="textTransform: none; letter-spacing: 0;"
                :dark="valid"
                :disabled="!valid"
                :block="$vuetify.breakpoint.xs"
                :loading="loading"
                @click="sendEmail()"
              >
                Send Message
              </v-btn>
            </v-card-text>
          </v-form>
        </v-card>
      </v-col>
    </v-row>

    <v-snackbar
      app
      text
      outlined
      v-model="snackbarShow"
      :color="color"
    >
      <v-layout
        align-center
        pr-4
      >
        <img
          :src="icon"
          class="mr-1"
          height="24"
          width="24"
        >

        {{ text }}
      </v-layout>

      <template
        v-slot:action="{ attrs }"
      >
        <v-btn
          icon
          v-bind="attrs"
          :color="color"
          @click="snackbarShow = false"
        >
          <v-icon>
            mdi-window-close
          </v-icon>
        </v-btn>
      </template>
    </v-snackbar>
  </v-container>
</template>

<style lang="scss" scoped>
.container {
  height: 100%;
}

h1 {
  font-size: 3.5rem;
  margin-bottom: 1rem;
}

h4 {
  color: #9E9E9E;
  margin-bottom: 20px;
}
</style>

<script>
import emailjs from 'emailjs-com';

export default {
  head() {
    return {
      title: "Contact",
    };
  },
  data: () => ({
    valid: false,
    loading: false,
    snackbarShow: false,
    text: '',
    icon: '',
    color: '',
    name: '',
    nameRules: [
      value => !!value
    ],
    email: '',
    emailRules: [
      value => !!value,
      value => /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{1,}))$/.test(value),
    ],
    message: '',
    messageRules: [
      value => !!value
    ],
    cards: [
      {
        icon: require("@/assets/icons/mail.svg"),
        text: "juliandpt98@gmail.com"
      },
      {
        icon: require("@/assets/icons/phone.svg"),
        text: "+34 620 69 69 68"
      }
    ]
  }),
  methods: {
    sendEmail: function () {
      this.loading = true

      var userParams = {
        from_name: this.name,
        from_email: this.email,
        message: this.message
      }

      emailjs.send('service_julian', 'template_julian', userParams, 'user_WjMXCOdbdqCzwQpCDkjtL')
      .then(
        (response) => {
          this.text = 'Email sent Successfuly!'
          this.icon = require("@/assets/icons/check-green.svg")
          this.color = 'green darken-2'
          this.snackbarShow = true
          this.loading = false
        },
        (error) => {
          this.text = 'An error ocurred'
          this.icon = require("@/assets/icons/error.svg")
          this.color = 'red'
          this.snackbarShow = true
          this.loading = false
        }
      )
    },
    copyText: function (text) {
      navigator.clipboard.writeText(text);
    }
  }
};
</script>