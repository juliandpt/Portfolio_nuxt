<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%' : ''"
  >
    <v-row>
      <v-col
        cols="12"
        md="6"
        sm="12"
        class="d-flex flex-column justify-center"
      >
        <svg viewBox="0 0 200 187" xmlns="http://www.w3.org/2000/svg">
          <path fill="#3F51B5" d="M38.6,22.9C25,45.8,-28.3,46.5,-41.3,23.8C-54.4,1.2,-27.2,-44.8,-0.5,-45.1C26.1,-45.4,52.2,-0.1,38.6,22.9Z" transform="translate(100 100)" />
        </svg>
        <!-- <img
        class="rounded"
        src="@/assets/images/profile.jpg"
        width="100px"
        height="100px"> -->
      </v-col>

      <v-col
        cols="12"
        md="4"
        sm="10"
        class="d-flex flex-column justify-center"
      >
        <p>Hello!</p>
        <h1>I'm Julián</h1>
        <h2>Software Engineer</h2>
        <p>caca</p>
        <div>
          <v-btn
            dark
            x-large
            color="indigo"
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
        md="2"
        sm="2"
        :class="$vuetify.breakpoint.xs ? 'd-flex justify-center' : 'd-flex flex-column justify-center align-center'"
      >
        <v-btn
          icon
          large
          fab
          color="indigo"
          href="https://www.linkedin.com/in/julián-de-pablo-torremocha"
          target="_blank"
        >
          <img
            src="@/assets/icons/linkedin.svg"
            height="28"
            width="28"
          >
        </v-btn>

        <v-btn 
          icon
          large
          fab
          color="indigo"
          href="https://github.com/julidpt"
          target="_blank"
        >
          <img
            src="@/assets/icons/github.svg"
            height="28"
            width="28"
          >
        </v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<style lang="scss" scoped>
.container,
.row {
  height: 100%;
}

h1 {
  font-family: 'Poppins', sans-serif;
  font-size: 350%;
}
</style>

<script>
export default {
  head() {
    return {
      title: "Home",
    };
  },
};
</script>