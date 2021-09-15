<template>
  <v-container
    class="d-flex align-center"
    :style="$vuetify.breakpoint.xl || $vuetify.breakpoint.sm ? 'padding: 0 15%' : ''"
  >
    <v-row>
      <v-col
        md="6"
        sm="12"
        class="d-flex flex-column justify-center"
      >
        <h1
          :class="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? 'mx-auto' : ''"
        >
          Contact me
        </h1>

        <h4
          :class="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? 'mx-auto' : ''"
        >
          Let's get in touch! &#129311;
        </h4>

        <v-card
          flat
          :class="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? 'd-flex align-center mt-3 py-4 px-2' : 'd-flex align-center mt-5 py-4 px-2'"
          v-for="(card, i) in cards"
          :key="i"
          :outlined="!$vuetify.theme.dark"
          :style="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? 'width: 100%;' : 'width: 18rem;'"
        >
          <img
            :src="card.icon"
            class="mx-3"
            height="24"
            width="24"
          >

          <v-card-text
            class="pa-0 grey--text"
            ref="textToCopy"
          >
            {{ card.text }}
          </v-card-text>
          
          <v-btn
            icon
            :disabled="card.copied"
            color="grey"
            @click="copyText(card.text, i)"
          >
            <v-scroll-x-transition
              hide-on-leave
            >
              <img
                height="24"
                width="24"
                src="@/assets/icons/check.svg"
                v-if="card.copied"
              >
            </v-scroll-x-transition>

            <v-scroll-x-transition
              hide-on-leave
            >
              <img
                height="24"
                width="24"
                src="@/assets/icons/copy.svg"
                v-if="!card.copied"
              >
            </v-scroll-x-transition>
          </v-btn>
        </v-card>
      </v-col>

      <v-col
        md="6"
        sm="12"
        :class="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? 'pt-0' : ''"
      >
        <v-card
          :outlined="!$vuetify.theme.dark"
          :class="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? 'pa-1' : 'pa-10'"
        >
          <v-form
            v-model="valid"
          >
            <v-card-title
              :style="$vuetify.breakpoint.xs ? '' : 'font-size: 30px;'"
              class="mb-10 py-0"
              :class="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? 'mb-10 pt-4' : 'mb-10 py-0'"
            >
              <span
                class="mx-auto"
              >
                Send me a message!
              </span>
            </v-card-title>

            <v-card-text
              class="pt-0"
            >
              <v-text-field
                filled
                rounded
                required
                clearable
                clear-icon="mdi-window-close"
                label="Name"
                hide-details="auto"
                class="rounded ma-0"
                color="primary"
                v-model="name"
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
                required
                clearable
                clear-icon="mdi-window-close"
                label="Email"
                placeholder="example@domain.com"
                hide-details="auto"
                class="rounded"
                color="primary"
                v-model="email"
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
                required
                clearable
                clear-icon="mdi-window-close"
                label="Message"
                class="rounded"
                color="primary"
                maxlength="500"
                v-model="message"
                :rules="messageRules"
              ></v-textarea>
            </v-card-text>

            <v-card-text
              class="pt-0"
            >
              <v-btn
                x-large
                color="primary"
                elevation="0"
                :dark="valid"
                :disabled="!valid"
                :block="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm"
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
      :text="!$vuetify.theme.dark"
      v-model="snackbarShow"
      :color="error ? 'red darken-3' : 'green darken-2'"
    >
      <v-layout
        align-center
        pr-4
      >
        <img
          src="@/assets/icons/error-white.svg"
          class="mr-1"
          height="24"
          width="24"
          v-if="error && $vuetify.theme.dark"
        >

        <img
          src="@/assets/icons/error.svg"
          class="mr-1"
          height="24"
          width="24"
          v-if="error && !$vuetify.theme.dark"
        >

        <img
          src="@/assets/icons/circle-check-white.svg"
          class="mr-1"
          height="24"
          width="24"
          v-if="!error && $vuetify.theme.dark"
        >

        <img
          src="@/assets/icons/circle-check-green.svg"
          class="mr-1"
          height="24"
          width="24"
          v-if="!error && !$vuetify.theme.dark"
        >

        {{ text }}
      </v-layout>

      <template
        v-slot:action="{ attrs }"
      >
        <v-btn
          icon
          v-bind="attrs"
          @click="snackbarShow = false"
        >
          <img
            src="@/assets/icons/close-white.svg"
            height="24"
            width="24"
            v-if="$vuetify.theme.dark"
          >

          <img
            src="@/assets/icons/close-red.svg"
            height="24"
            width="24"
            v-if="!$vuetify.theme.dark && error"
          >

          <img
            src="@/assets/icons/close-green.svg"
            height="24"
            width="24"
            v-if="!$vuetify.theme.dark && !error"
          >
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
    error: false,

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
        text: "juliandpt98@gmail.com",
        copied: false
      },
      {
        icon: require("@/assets/icons/phone.svg"),
        text: "+34 620 69 69 68",
        copied: false
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
          this.snackbarShow = true
          this.loading = false
        },
        (error) => {
          this.text = 'An error ocurred'
          this.error = true
          this.snackbarShow = true
          this.loading = false
        }
      )
    },
    copyText: function (text, i) {
      navigator.clipboard.writeText(text);

      this.cards[i].copied = true

      setTimeout (() => {
        this.cards[i].copied = false
      }, 3000)
    }
  }
};
</script>