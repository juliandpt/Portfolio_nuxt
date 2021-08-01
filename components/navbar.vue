<template>
  <v-container
    v-if="!$vuetify.breakpoint.xs"
  >
    <v-card
      color="transparent"
      flat
    >
      <v-toolbar
        color="transparent"
        flat
      >
        <v-toolbar-title> Julián de Pablo </v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn
          to="/"
          text
          style="textTransform: none; letter-spacing: 0;"
        >
          Home
        </v-btn>

        <v-btn
          to="/about"
          text
          style="textTransform: none; letter-spacing: 0;"
        >
          About
        </v-btn>

        <v-btn
          to="/skills"
          text
          style="textTransform: none; letter-spacing: 0;"
        >
          Skills
        </v-btn>

        <v-btn
          to="/contact"
          text
          style="textTransform: none; letter-spacing: 0;"
        >
          Contact
        </v-btn>

        <v-spacer></v-spacer>

        <v-btn
          icon
          color="indigo"
          href="https://www.instagram.com/julidpt"
          target="_blank"
        >
          <img
            src="@/assets/icons/instagram.svg"
            alt="instagram" 
            height="24"
            width="24"
          >
        </v-btn>

        <v-btn
          icon
          color="indigo"
          href="https://twitter.com/Depabloj"
          target="_blank"
        >
          <img
            src="@/assets/icons/twitter.svg"
            alt="twitter" 
            height="24"
            width="24"
          >
        </v-btn>

        <v-btn
          icon
          color="indigo"
          href="https://www.facebook.com/juli.depablo"
          target="_blank"
        >
          <img
            src="@/assets/icons/facebook.svg"
            alt="facebook"
            height="24"
            width="24"
          >
        </v-btn>

        <v-divider
          inset
          vertical
          class="mx-1"
        ></v-divider>
        
        <v-btn
          icon
          color="indigo"
          v-if="!$vuetify.theme.dark"
          @click="toggleTheme()"
        >
          <img
            src="@/assets/icons/moon.svg"
            alt="facebook"
            height="24"
            width="24"
          >
        </v-btn>

        <v-btn
          icon
          color="indigo"
          v-else
          @click="toggleTheme()"
        >
          <img
            src="@/assets/icons/sun.svg"
            alt="facebook"
            height="30"
            width="30"
          >
        </v-btn>
      </v-toolbar> 
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
