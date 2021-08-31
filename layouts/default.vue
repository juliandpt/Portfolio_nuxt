<template>
  <v-app>
    <navbar
      v-show="$route.name !== 'dashboard' && $route.name !== 'login'"
    />

    <v-main>
      <nuxt />
    </v-main>

    <foot
      v-show="$route.name !== 'dashboard' && $route.name !== 'login'"
    />
  </v-app>
</template>

<style scoped>
#app {
  font-family: 'Poppins', sans-serif;
}
</style>