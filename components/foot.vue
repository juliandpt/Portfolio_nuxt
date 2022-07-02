<template>
  <v-container>
    <v-footer
      padless
      color="transparent"
      v-if="$vuetify.breakpoint.xs"
    >
      <v-card
        flat
        tile
        width="100%"
        color="transparent"
        class="text-center"
      >
        <v-card-text
          class="pa-0"
        >
          <v-btn
            icon
            large
            color="indigo"
            class="mx-1"
            v-for="(social, i) in socials"
            :key="i"
            :href="social.link"
            target="_blank"
          >
            <img
              :src="social.icon"
              :alt="social.alt"
              height="24"
              width="24"
            >
          </v-btn>
        </v-card-text>

        <v-card-text
          class="pa-0"
        >
          Julián de Pablo © {{ new Date().getFullYear() }}. All rights reserved
        </v-card-text>
      </v-card>
    </v-footer>

    <v-footer
      padless
      color="transparent"
      v-else
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
              rel="noopener noreferrer"
            >
              <img
                :src="social.icon"
                :alt="social.alt"
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
        icon: "/icons/instagram.svg",
        link: "https://www.instagram.com/julidpt",
        alt: "instagram"
      },
      {
        icon: "/icons/twitter.svg",
        link: "https://twitter.com/Depabloj",
        alt: "twitter"
      },
      {
        icon: "/icons/facebook.svg",
        link: "https://www.facebook.com/juli.depablo",
        alt: "facebook"
      },
      {
        icon: "/icons/linkedin.svg",
        link: 'https://www.linkedin.com/in/juliandepablo',
        alt: "linkedin"
      }
    ]
  })
}
</script>