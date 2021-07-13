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
          class="d-flex align-center mb-5"
          :style="$vuetify.breakpoint.xs ? 'padding: 1rem 0.5rem; width: 100%; border-radius:20px;' : 'padding: 1rem 0.5rem; width: auto; max-width: 16rem; border-radius:20px;'"
        >
          <img
            src="@/assets/icons/mail.svg"
            class="mx-3"
            height="24"
            width="24"
          >

          <v-card-text
            class="pa-0"
          >
            juliandpt98@gmail.com
          </v-card-text>
        </v-card>

        <v-card
          flat
          class="d-flex align-center mb-5"
          :style="$vuetify.breakpoint.xs ? 'padding: 1rem 0.5rem; width: 100%; border-radius:20px;' : 'padding: 1rem 0.5rem; width: auto; max-width: 16rem; border-radius:20px;'"
        >
          <img
            src="@/assets/icons/phone.svg"
            class="mx-3"
            height="24"
            width="24"
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
        sm="6"
      >
        <v-card
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
              label="name"
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
              label="email"
              placeholder="example@gmail.com"
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
              elevation="0"
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

.rounded-card{
  border-radius:1.2rem;
  padding: 2.5rem;
}

.v-input__control {
  margin: 0;
  background-color: #f7f6ff;
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