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
          height="auto"
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
          width="100%"
          :max-width="$vuetify.breakpoint.xs ? '100%' : '75%'"
        >
          <v-form
            v-model="valid"
          >
            <v-card-title
              :class="$vuetify.breakpoint.xs ? 'justify-center' : 'mb-5'"
            >
              <h1>
                Hello, Me!
              </h1>
            </v-card-title>

            <v-card-subtitle
              :class="$vuetify.breakpoint.xs ? 'mb-5 mt-0 text-center primary--text' : 'mb-5 primary--text'"
            >
              <span>
                Sign in to acces to the portfolio dashboard
              </span>
            </v-card-subtitle>

            <v-card-text
              class="pt-6 pb-3"
            >
              <v-text-field
                outlined
                required
                hide-details
                clearable
                clear-icon="mdi-window-close"
                label="Email"
                color="primary"
                v-model="email"
                :append-icon="email == '' || email == null ? 'mdi-email-outline' : ''"
                :rules="emailRules"
              >
              </v-text-field>
            </v-card-text>

            <v-card-text
              class="pt-6 pb-3"
            >
              <v-text-field
                outlined
                auto-grow
                required
                hide-details
                label="Password"
                color="primary"
                v-model="password"
                @click:append="show = !show"
                :append-icon="show ? 'mdi-lock-open-variant-outline' : 'mdi-lock-outline'"
                :type="show ? 'text' : 'password'"
                :rules="passwordRules"
              ></v-text-field>
            </v-card-text>

            <v-card-text
              class="py-6"
            >
              <v-btn
                block
                x-large
                color="primary"
                elevation="0"
                style="textTransform: none; letter-spacing: 0;"
                :dark="valid"
                :disabled="!valid"
                :loading="loading"
                @click="login"
              >
                Sign in
              </v-btn>
            </v-card-text>
          </v-form>

          <p
            class="mx-4 my-0 text-center"
          >
            - or -
          </p>

          <v-card-text
              class="py-6 d-flex"
            >
              <v-col
                md="6"
                class="pl-0 py-0"
              >
                <v-btn
                  x-large
                  block
                  color="error"
                  elevation="0"
                  style="textTransform: none; letter-spacing: 0;"
                  :outlined="!$vuetify.theme.dark"
                  to="/"
                >
                  <img
                    src="@/assets/icons/arrow-back-white.svg"
                    height="18"
                    width="18"
                    class="ml-n1 mr-2"
                    v-if="$vuetify.theme.dark"
                  >

                  <img
                    src="@/assets/icons/arrow-back.svg"
                    height="18"
                    width="18"
                    class="ml-n1 mr-2"
                    v-if="!$vuetify.theme.dark"
                  >

                  Home
                </v-btn>
              </v-col>

              <v-col
                md="6"
                class="pr-0 py-0"
              >
                <v-btn
                  x-large
                  block
                  dark
                  color="blue darken-4"
                  elevation="0"
                  style="textTransform: none; letter-spacing: 0;"
                  @click="loginWithGoogle"
                >
                  <v-icon
                    left
                  >
                    mdi-google
                  </v-icon>

                  Google
                </v-btn>
              </v-col>
            </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  head() {
    return {
      title: "Sign in",
    };
  },
  data() {
    return {
      valid: false,

      loading: false,

      error: false,

      show: false,
      
      email: '',
      emailRules: [
        value => !!value,
        value => /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{1,}))$/.test(value),
      ],
      password: '',
      passwordRules: [
        value => !!value
      ],
    }
  },
  methods: {
    login() {
      this.$fire.auth.signInWithEmailAndPassword(this.email, this.password)
        .then((userCredential) => {
          console.log(userCredential)
          this.$router.push("/dashboard")
        })
        .catch((error) => {
          var errorCode = error.code;
          var errorMessage = error.message;
          console.error(errorCode, errorMessage)
        });
    },
    loginWithGoogle() {
      var provider = new this.$fire.auth.GoogleAuthProvider();

      this.$fire.auth().signInWithPopup(provider)
        .then((result) => {
          var credential = result.credential;
          var token = credential.accessToken;
          var user = result.user;
        }).catch((error) => {
          var errorCode = error.code;
          var errorMessage = error.message;
          var email = error.email;
          var credential = error.credential;
        })
    }
  }
};
</script>