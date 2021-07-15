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
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%' : ''"
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
          <span>Julián © {{ new Date().getFullYear() }}. All rights reserved</span>

          <v-spacer></v-spacer>

          <span>caca</span>
        </v-card-title>
      </v-card>
    </v-footer>
  </v-container>
</template>

// <script>
// import backgroundUrl from "~/assets/images/waves.svg";

// export default {
//   data() {
//     return {
//       backgroundUrl,
//     };
//   },
// };
//
// :style="{ backgroundImage: `url(${backgroundUrl})` }"
//
// :style="[ $vuetify.breakpoint.xl ? 'padding: 0 15%' : '', { backgroundImage: `url(${backgroundUrl})` }]"
// </script>