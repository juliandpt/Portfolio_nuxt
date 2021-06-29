<template>
  <v-app-bar fixed flat color="transparent">
    <v-toolbar-title> Julian </v-toolbar-title>

    <v-spacer></v-spacer>

    <v-toolbar-items>
      <v-btn to="/" text> Home </v-btn>
      <v-btn to="/about" text> About </v-btn>
      <v-btn to="/skills" text> Skills </v-btn>
      <v-btn to="/contact" text> Contact </v-btn>
    </v-toolbar-items>

    <v-switch
      v-model="$vuetify.theme.dark"
      color="indigo"
      hide-details
    ></v-switch>
  </v-app-bar>
</template>

<style lang="sass">
</style>