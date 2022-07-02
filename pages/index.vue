<template>
  <v-container
    :style="$vuetify.breakpoint.xl || $vuetify.breakpoint.sm ? 'padding: 0 15%' : ''"
  >
    <v-row>
      <v-col
        cols="12"
        md="6"
        sm="12"
        :order="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? '2' : '1'"
        :class="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? 'd-flex flex-column justify-center align-center' : 'd-flex flex-column justify-center'"
      >
        <h1
          style="font-size: 4em;"
        >
          I'm 

          <span 
            class="primary--text"
          >
            Julián
          </span>
        </h1>

        <vue-typed-js
          :strings="['Fullstack Developer', 'Web Designer', 'Software Engineer']"
          :loop="true"
          :backSpeed="40"
          :cursorChar="'_'"
        >
          <h2>
            <span class="typing"></span>
          </h2>
        </vue-typed-js>
        
        <div
          class="mt-12"
        >
          <v-btn
            dark
            large
            outlined
            elevation="0"
            color="primary"
            to="/contact"
          >
            Contact me

            <img
              src="/icons/arrow.svg"
              alt="arrow"
              height="18"
              width="18"
              class="mr-n1 ml-2"
            >
          </v-btn>

          <v-btn
              dark
              large
              elevation="0"
              color="primary"
              class="ml-4"
              href="Julián-CV.pdf"
              download
            >
              Download CV

              <img
                src="/icons/download.svg"
                alt="download"
                height="18"
                width="18"
                class="mr-n1 ml-2"
              >
            </v-btn>
        </div>

        <div
          :style="$vuetify.breakpoint.xs ? 'margin-top: 3em' : 'margin-top: 4em; margin-left:-1em;'"
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
            rel="noopener noreferrer"
          >
            <img
              :src="social.icon"
              :alt="social.alt"
              height="28"
              width="28"
            >
          </v-btn>
        </div>
      </v-col>

      <v-col
        cols="12"
        md="6"
        sm="12"
        class="d-flex flex-column justify-center"
        :order="$vuetify.breakpoint.xs || $vuetify.breakpoint.sm ? '1' : '2'"
      >
        <v-img
          contain
          src="/images/index.png"
          height="auto"
          class="shadow"
        ></v-img>
      </v-col>
    </v-row>
  </v-container>
</template>


<style scoped>
.container,
.row {
  height: 100%;
}
</style>


<script>
import Vue from 'vue'
import VueTypedJs from 'vue-typed-js'

Vue.use(VueTypedJs)

export default {
  head() {
    return {
      title: "Home",
    };
  },
  data: () => ({
    socials: [
      {
        icon: "/icons/linkedin.svg",
        link: 'https://www.linkedin.com/in/juliandepablo',
        alt: "linkedin"
      },
      {
        icon: "/icons/dribbble.svg",
        link: 'https://dribbble.com/juliandpt',
        alt: "dribbble"
      },
      {
        icon: "/icons/github.svg",
        link: 'https://github.com/juliandpt',
        alt: "github"
      }
    ]
  })
};
</script>