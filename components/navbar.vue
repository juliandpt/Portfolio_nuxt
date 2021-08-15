<template>
  <v-container
    v-if="!$vuetify.breakpoint.xs"
  >
    <v-card
      flat
      color="transparent"
    >
      <v-app-bar
        flat
        color="transparent"
      >
        <v-toolbar-title> Julián de Pablo </v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn
          text
          to="/"
          style="textTransform: none; letter-spacing: 0;"
        >
          Home
        </v-btn>

        <v-btn
          text
          to="/about"
          style="textTransform: none; letter-spacing: 0;"
        >
          About
        </v-btn>

        <v-btn
          text
          to="/skills"
          style="textTransform: none; letter-spacing: 0;"
        >
          Skills
        </v-btn>

        <v-btn
          text
          to="/contact"
          style="textTransform: none; letter-spacing: 0;"
        >
          Contact
        </v-btn>

        <v-btn
          icon
          plain
          color="indigo"
          v-if="!$vuetify.theme.dark"
          @click="toggleTheme()"
        >
          <img
            src="@/assets/icons/moon-dark.svg"
            alt="facebook"
            height="24"
            width="24"
          >
        </v-btn>

        <v-btn
          icon
          plain
          color="indigo"
          v-else
          @click="toggleTheme()"
        >
          <img
            src="@/assets/icons/sun-white.svg"
            alt="facebook"
            height="30"
            width="30"
          >
        </v-btn>
      </v-app-bar>
    </v-card>
  </v-container>
</template>

<style lang="scss">
.v-btn--active {
  background-color: transparent !important;
  color: #3f51b5 !important;
}

.v-input__control {
  margin: 0 0 0 0.5em;
}
</style>

<script>
export default({
  methods: {
    toggleTheme: function () {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    }
  }
})
</script>
