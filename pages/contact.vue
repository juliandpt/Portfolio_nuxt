<template>
  <v-container
    class="d-flex align-center"
    style="padding: 0 10%"
  >
    <v-row>
      <v-col
        md="6"
        sm="12"
        class="d-flex flex-column justify-center"
      >
        <h1 class="text-bol">
          Contact me
        </h1>

        <h4>
          Let's get in touch! 🤟
        </h4>

        <v-card 
          elevation="2"
          class="d-flex align-center card"
        >
          <img
            src="@/assets/icons/mail.svg"
            alt="chevron-down" 
            class="mx-3"
            style="height: 24px; width:24px;"
          >

          <v-card-text
            class="px-0 pt-0 pb-0"
          >
            juliandpt98@gmail.com
          </v-card-text>
        </v-card>

        <v-card
          elevation="2"
          class="d-flex align-center card"
        >
          <img
            src="@/assets/icons/phone.svg"
            alt="chevron-down" 
            class="mx-3"
            style="height: 24px; width:24px;"
          >

          <v-card-text
            class="px-0 pt-0 pb-0"
          >
            +34 620 69 69 68
          </v-card-text>
        </v-card>
      </v-col>

      <v-col
        md="6"
        sm="12"
        xs="12"
      >
        <v-card
          outlined
          class="rounded-card"
        >
          <v-card-title
            style="font-size: 30px, padding-top: 0; padding-bottom: 0; margin-bottom: 40px;"
          >
          Send me a message 🚀
          </v-card-title>

          <v-card-text
            class="pt-0"
          >
            <v-text-field
              filled
              rounded
              clearable
              clear-icon="mdi-window-close"
              label="Name"
              hide-details="auto"
              class="rounded"
              :color="$vuetify.theme.dark ? 'white' : 'indigo'"
              :rules="[rules.required]"
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
              clear-icon="mdi-window-close"
              label="Email"
              hide-details="auto"
              class="rounded"
              :color="$vuetify.theme.dark ? 'white' : 'indigo'"
              :rules="[rules.required, rules.email]"
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
              clear-icon="mdi-window-close"
              maxlength="500"
              label="Message"
              class="rounded"
              :color="$vuetify.theme.dark ? 'white' : 'indigo'"
              :rules="[rules.required]"
            ></v-textarea>
          </v-card-text>

          <v-card-text
            class="pt-0"
          >
            <v-btn 
              dark
              x-large
              color="indigo"
              elevation="5"
            >
              Send Message
            </v-btn>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style lang="scss" scoped>
.container {
  height: 100%;
}

.card {
  margin: 0 0 1rem 0;
  padding: 1rem 0.5rem;
  width: auto;
  max-width: 16rem;
  border-radius:20px;
}

.rounded-card{
  border-radius:20px;
  padding: 40px;
}

.v-input__control {
  margin: 0;
  background-color: #f7f6ff;
}

h1 {
  font-size: 52px;
  margin-bottom: 30px;
}

h4 {
  color: #9E9E9E;
  margin-bottom: 20px;
}

@media (max-width: 400px) {
  .card {
    max-width: 100%;
    min-width: 100%;
  }
}
</style>

<script>
export default {
  head() {
    return {
      title: "Contact",
    };
  },
  data: () => ({
      rules: {
        required: value => !!value || 'This field is required',
        counter: value => value.length <= 20 || 'Max 20 characters',
        email: value => {
          const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{1,}))$/
          return pattern.test(value) || 'Invalid e-mail.'
        },
      },
    }),
};
</script>