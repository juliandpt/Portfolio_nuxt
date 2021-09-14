<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%' : ''"
  >
    <v-row>
      <v-col
        cols="12"
        md="2"
        sm="2"
        :order="$vuetify.breakpoint.xs ? '3' : '1'"
        :class="$vuetify.breakpoint.xs ? 'd-flex justify-center mb-12' : 'd-flex flex-column justify-center'"
      >
        <v-btn
          icon
          large
          fab
          color="indigo"
          v-for="(social, i) in socials"
          :key="i"
          :href="social.link"
          target="_blank"
        >
          <img
            :src="social.icon"
            height="28"
            width="28"
          >
        </v-btn>
       </v-col>

      <v-col
        cols="12"
        md="4"
        sm="10"
        order="2"
        :class="$vuetify.breakpoint.xs ? 'd-flex flex-column justify-center align-center' : 'd-flex flex-column justify-center'"
      >
        <h1>Hello!</h1>

        <h1>
          I'm 

          <span 
            class="primary--text"
          >
            Julián
          </span>
        </h1>

        <h1>Software Engineer</h1>
        
        <div
          class="mt-10"
        >
          <v-btn
            dark
            x-large
            elevation="0"
            color="primary"
            to="/contact"
          >
            Contact me

            <img
              src="@/assets/icons/send-white.svg"
              height="18"
              width="18"
              class="mr-n1 ml-2"
            >
          </v-btn>
        </div>
      </v-col>

      <v-col
        cols="12"
        md="6"
        sm="12"
        :order="$vuetify.breakpoint.xs ? '1' : '3'"
        class="d-flex flex-column justify-center"
      >
        <img
          src="@/assets/images/me.svg"
        >
      </v-col>
    </v-row>
  </v-container>
</template>

<style lang="scss" scoped>
.container,
.row {
  height: 100%;
}
</style>

<script>
export default {
  head() {
    return {
      title: "Home",
    };
  },
  data: () => ({
    socials: [
      {
        icon: require("@/assets/icons/linkedin.svg"),
        link: 'https://www.linkedin.com/in/julián-de-pablo-torremocha'
      },
      {
        icon: require("@/assets/icons/dribbble.svg"),
        link: 'https://dribbble.com/juliandpt'
      },
      {
        icon: require("@/assets/icons/github.svg"),
        link: 'https://github.com/juliandpt'
      }
    ]
  })
};
</script>