<template>
  <v-footer padless>
    <v-card
      flat
      tile
      class="footer text-center flex"
    >
      <v-card-text>
        <v-btn
          icon
          class="mx-4"
          href="https://www.facebook.com/juli.depablo"
          target="_blank"
        >
          <v-icon 
            size="24px"
          >
            mdi-facebook
          </v-icon>
        </v-btn>

        <v-btn
          icon
          class="mx-4"
          href="https://twitter.com/Depabloj"
          target="_blank"
        >
          <v-icon
            size="24px"
          >
            mdi-twitter
          </v-icon>
        </v-btn>

        <v-btn
          icon
          class="mx-4"
          href="https://www.instagram.com/julidpt"
          target="_blank"
        >
          <v-icon
            size="24px"
          >
            mdi-instagram
          </v-icon>
        </v-btn>
        
      </v-card-text>

      <v-card-text>
        © {{ new Date().getFullYear() }} Portfolio. All rights reserved
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<style>
</style>