<template>
  <v-container
    class="d-flex align-center"
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%; height: 100%;' : 'height: 100%;'"
  >
    <v-row>

      <v-col
        md=6
        sm=12
        class="d-flex justify-center align-center"
        v-if="!$vuetify.breakpoint.xs || $vuetify.breakpoint.sm"
      >
        <img
          src="@/assets/images/pc.png"
          height="100%"
          width="100%"
        >
      </v-col>

      <v-col
        md=6
        sm=12
        class="d-flex align-center justify-end"
      >
        <v-card
          color="transparent"
          elevation="0"
          class="pa-0"
          min-width="75%"
          :max-width="$vuetify.breakpoint.xs ? '' : '75%'"
        >
          <v-form
            v-model="valid"
          >
            <v-card-title
              class="mb-10 py-0"
            >
              <h1 
                class="mb-5"
              >
                Log in
              </h1>
            </v-card-title>

            <v-card-subtitle>
              
            </v-card-subtitle>

            <v-card-text
              class="py-6"
            >
              <v-text-field
                outlined
                auto-grow
                required
                hide-details="auto"
                label="Email"
                color="indigo accent-2"
                v-model="email"
                :rules="emailRules"
              >
              </v-text-field>
            </v-card-text>

            <v-card-text
              class="py-6"
            >
              <v-text-field
                outlined
                auto-grow
                required
                hide-details="auto"
                label="Password"
                color="indigo accent-2"
                v-model="password"
                :rules="passwordRules"
              ></v-text-field>
            </v-card-text>

            <v-card-text
              class="py-6"
              style="margin: 0 0 0 0.5em;"
            >
              <v-btn
                block
                x-large
                color="indigo"
                elevation="0"
                style="textTransform: none; letter-spacing: 0;"
                :dark="valid"
                :disabled="!valid"
                :loading="loading"
                @click="login()"
              >
                Send Message
              </v-btn>
            </v-card-text>
          </v-form>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
</style>

<script>
export default {
  head() {
    return {
      title: "Contact",
    };
  },
  data: () => ({
    valid: false,

    loading: false,

    error: false,

    
    email: '',
    emailRules: [
      value => !!value,
      value => /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{1,}))$/.test(value),
    ],
    password: '',
    passwordRules: [
      value => !!value
    ],
  }),
  methods: {
    login: () => {

    }
  }
};
</script>