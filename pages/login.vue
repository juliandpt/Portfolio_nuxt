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
                Sign in to access to the portfolio dashboard
              </span>
            </v-card-subtitle>

            <v-card-text
              class="pt-0 pb-3"
            >
              <v-text-field
                outlined
                required
                clearable
                persistent-hint
                clear-icon="mdi-window-close"
                label="Enter your email"
                color="primary"
                v-model="email"
                :error="errorEmail"
                :append-icon="email === '' || email == null ? 'mdi-email-outline' : ''"
                :error-messages="errorEmail ? errorEmailMessage : ''"
                @keyup.enter="login()"
              >
              </v-text-field>
            </v-card-text>

            <v-card-text
              class="pt-0 pb-3"
            >
              <v-text-field
                outlined
                auto-grow
                required
                persistent-hint
                label="Enter your password"
                color="primary"
                v-model="password"
                @click:append="show = !show"
                :append-icon="show ? 'mdi-lock-open-variant-outline' : 'mdi-lock-outline'"
                :type="show ? 'text' : 'password'"
                :error="errorPassword"
                :error-messages="errorPassword ? errorPasswordMessage : ''"
                @keyup.enter="login()"
              ></v-text-field>
            </v-card-text>

            <v-card-text
              class="pt-0 pb-4"
            >
              <v-btn
                block
                x-large
                color="primary"
                elevation="0"
                dark
                :loading="loading"
                @click="login()"
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
              class="d-flex"
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
import firebase from 'firebase'
import 'firebase/auth'

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

      errorEmail: false,
      errorEmailMessage: "",
      errorPassword: false,
      errorPasswordMessage: "",

      show: false,
      
      email: "",
      password: "",
    }
  },
  methods: {
    login() {
      this.loading = true

      if (this.email === "") {
        this.loading = false
        this.errorPassword = false
        this.errorEmailMessage = "Enter your email"
        this.errorEmail = true
      }
      else if (this.password === "") {
        this.loading = false
        this.errorEmail = false
        this.errorPasswordMessage = "Enter a password"
        this.errorPassword = true
      }
      else{
        this.$fire.auth.signInWithEmailAndPassword(this.email, this.password)
          .then((userCredential) => {
            console.log(userCredential)
            this.$router.push("/dashboard")
          })
          .catch((error) => {
            this.loading = false
            if (error.code === 'auth/invalid-email') {
              this.errorPassword = false
              this.errorEmailMessage = "invalid email format"
              this.errorEmail = true
            }
            else if (error.code === 'auth/user-not-found') {
              this.errorPassword = false
              this.errorEmailMessage = "Couldn't find yout account"
              this.errorEmail = true
            }
            else {
              this.errorEmail = false
              this.errorPasswordMessage = "Wrong password. Try again or click ‘Forgot password’"
              this.errorPassword = true
            }
          });
      }
    },
    loginWithGoogle() {
      var provider = new firebase.auth.GoogleAuthProvider();

      firebase.auth().signInWithPopup(provider)
        .then((result) => {
          console.log(result)
          this.$router.push("/dashboard")
        }).catch((error) => {
          console.log(error)
        })
    }
  }
};
</script>