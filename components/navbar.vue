<template>
  <v-container>
    <v-card color="transparent" flat>
      <v-toolbar color="transparent" flat>
        <v-toolbar-title> Juliandpt </v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn to="/" text> <v-icon left> mdi-home </v-icon>Home </v-btn>

        <v-btn to="/about" text>
          <v-icon left> mdi-information-outline </v-icon>About
        </v-btn>

        <v-btn to="/skills" text>
          <v-icon left> mdi-laptop </v-icon>Skills
        </v-btn>

        <v-btn to="/contact" text>
          <v-icon left> mdi-at </v-icon>Contact
        </v-btn>

        <v-switch
          v-model="$vuetify.theme.dark"
          color="indigo"
          hide-details
          inset
        ></v-switch>
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
  margin: 0 1em;
}

.v-toolbar__title {
  font-family: "Caveat", cursive;
  font-size: 3rem;
  padding: 0 0.1em;
}
</style>