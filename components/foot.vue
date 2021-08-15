<template>
  <v-bottom-navigation
    app
    v-if="$vuetify.breakpoint.xs"
    style="z-index: 999;"
    color="transparent"
  >
    <v-btn to="/">
      <img
        src="@/assets/icons/home.svg"
        alt="instagram"
        height="24"
        width="24"
      >
    </v-btn>

    <v-btn to="/about">
      <img
        src="@/assets/icons/info.svg"
        alt="instagram" 
        height="24"
        width="24"
      >
    </v-btn>

    <v-btn to="/skills">
      <img
        src="@/assets/icons/laptop.svg"
        alt="instagram" 
        height="24"
        width="24"
      >
    </v-btn>

    <v-btn to="/contact">
      <img
        src="@/assets/icons/at.svg"
        alt="instagram" 
        height="24"
        width="24"
      >
    </v-btn>
  </v-bottom-navigation>

  <v-container
    v-else
  >
    <v-footer
      padless
      color="transparent"
    >
      <v-card
        flat
        tile
        color="transparent"
        class="flex"
      >
        <v-card-title>
          <span>
            Julián de Pablo © {{ new Date().getFullYear() }}. All rights reserved
          </span>

          <v-spacer></v-spacer>

          <div>
            <v-btn
              icon
              large
              color="indigo"
              v-for="(social, i) in socials"
              :key="i"
              :href="social.link"
              target="_blank"
            >
              <img
                :src="social.icon"
                height="24"
                width="24"
              >
            </v-btn>
          </div>
        </v-card-title>
      </v-card>
    </v-footer>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    socials: [
      {
        icon: require("@/assets/icons/instagram.svg"),
        link: "https://www.instagram.com/julidpt"
      },
      {
        icon: require("@/assets/icons/twitter.svg"),
        link: "https://twitter.com/Depabloj"
      },
      {
        icon: require("@/assets/icons/facebook.svg"),
        link: "https://www.facebook.com/juli.depablo"
      },
      {
        icon: require("@/assets/icons/linkedin.svg"),
        link: 'https://www.linkedin.com/in/julián-de-pablo-torremocha'
      }
    ]
  })
}
</script>