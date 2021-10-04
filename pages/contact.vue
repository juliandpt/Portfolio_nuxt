<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%' : ''"
  >
    <v-row
      class="mt-8 mb-8 d-flex flex-column justify-center"
    >
      <h1
        class="mx-auto mb-0"
      >
        Contact me
      </h1>

      <p
        class="mx-auto secondary--text"
      >
        Let's get in touch!
      </p>
    </v-row>

    <v-row>
      <v-col
        md="6"
        sm="6"
        class="d-flex flex-column align-center"
        :order="$vuetify.breakpoint.xs ? '2' : '1'"
      >
        <v-card
          flat
          height="50"
          elevation="0"
          color="transparent"
          class="d-flex align-center mb-4"
          v-for="(card, i) in cards"
          :key="i"
          :width="$vuetify.breakpoint.xs ? '100%' : '18rem'"
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
            color="grey"
            x-large
            v-if="card.canCopy"
            :disabled="card.copied"
            @click="copyText(card.text, i)"
          >
            <v-scroll-x-transition
              hide-on-leave
            >
              <img
                height="24"
                width="24"
                src="/icons/check.svg"
                v-if="card.copied"
              >
            </v-scroll-x-transition>

            <v-scroll-x-transition
              hide-on-leave
            >
              <img
                height="24"
                width="24"
                src="/icons/copy.svg"
                v-if="!card.copied"
              >
            </v-scroll-x-transition>
          </v-btn>
        </v-card>
      </v-col>

      <v-col
        md="6"
        sm="6"
        :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
        :order="$vuetify.breakpoint.xs ? '1' : '2'"
      >
        <v-card
          color="transparent"
          elevation="0"
          :class="$vuetify.breakpoint.sm ? 'pr-8' : ''"
        >
          <v-form
            v-model="valid"
          >
            <v-card-text
              class="pt-0 px-0"
            >
              <v-row>
                <v-col
                  cols="12"
                  md="6"
                  sm="12"
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
                </v-col>

                <v-col
                  cols="12"
                  md="6"
                  sm="12"
                  :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
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
                </v-col>
              </v-row>

              <v-row>
                <v-col
                  :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
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
                    rows="8"
                    v-model="message"
                    :rules="messageRules"
                  ></v-textarea>
                </v-col>
              </v-row>
            </v-card-text>

            <v-card-text
              class="pt-0 px-0"
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
          src="/icons/error-white.svg"
          class="mr-1"
          height="24"
          width="24"
          v-if="error && $vuetify.theme.dark"
        >

        <img
          src="/icons/error.svg"
          class="mr-1"
          height="24"
          width="24"
          v-if="error && !$vuetify.theme.dark"
        >

        <img
          src="/icons/circle-check-white.svg"
          class="mr-1"
          height="24"
          width="24"
          v-if="!error && $vuetify.theme.dark"
        >

        <img
          src="/icons/circle-check-green.svg"
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
            src="/icons/close-white.svg"
            height="24"
            width="24"
            v-if="$vuetify.theme.dark"
          >

          <img
            src="/icons/close-red.svg"
            height="24"
            width="24"
            v-if="!$vuetify.theme.dark && error"
          >

          <img
            src="/icons/close-green.svg"
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
  min-height: 100%;
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
        icon: "/icons/mail.svg",
        text: "juliandpt98@gmail.com",
        canCopy: true,
        copied: false
      },
      {
        icon: "/icons/phone.svg",
        text: "+34 620 69 69 68",
        canCopy: true,
        copied: false
      },
      {
        icon: "/icons/location.svg",
        text: "Madrid, Spain",
        canCopy: false,
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