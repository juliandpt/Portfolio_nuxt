<template>
  <v-container>
    <v-row
      cols="12"
    >
      <v-col
        md="5"
        sm="12"
        xs="12"
        class="d-flex flex-column justify-center"
      >
          <svg viewBox="0 0 200 187" xmlns="http://www.w3.org/2000/svg">
            <path fill="#3F51B5" d="M38.6,22.9C25,45.8,-28.3,46.5,-41.3,23.8C-54.4,1.2,-27.2,-44.8,-0.5,-45.1C26.1,-45.4,52.2,-0.1,38.6,22.9Z" transform="translate(100 100)" />
          </svg>
      </v-col>

      <v-col
        md="4"
        sm="12"
        xs="12"
        class="d-flex flex-column justify-center"
      >
        <h1>Hi! I'm Julián</h1>
        <h2>Software Engineer</h2>
        <p>caca</p>
        <div>
          <v-btn 
            dark
            x-large
            color="indigo"
            elevation="5"
            to="/contact"
          >
            Contact me

            <v-icon 
              right
            >
              mdi-send
            </v-icon>
          </v-btn>
        </div>
      </v-col>

      <v-col
        md="3"
        sm="12"
        xs="12"
        class="d-flex flex-column justify-center"
      >
        <v-btn
          icon
          large
          fab
          color="indigo"
          href="https://www.linkedin.com/in/julián-de-pablo-torremocha"
          target="_blank"
        >
          <v-icon> 
            mdi-linkedin 
          </v-icon>
        </v-btn>

        <v-btn 
          icon
          large
          fab
          color="indigo"
          href="https://github.com/julidpt"
          target="_blank"
        >
          <v-icon> 
            mdi-github 
          </v-icon>
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