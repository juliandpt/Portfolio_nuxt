<template>
  <v-app>
    <navbar
      v-show="$route.name !== 'dashboard'"
    />

    <v-main>
      <nuxt />
    </v-main>

    <foot
      v-show="$route.name !== 'dashboard'"
    />
  </v-app>
</template>

<style scoped>
#app {
  font-family: 'Poppins', sans-serif;
}
</style>