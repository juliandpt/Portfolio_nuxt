<template>
  <v-app>
    <navbar />

    <v-main>
      <nuxt />
    </v-main>

    <foot />
  </v-app>
</template>

<style scoped>
#app {
  font-family: 'Poppins', sans-serif;
}
/* width */
::-webkit-scrollbar {
  width: 5px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #ff2929;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: rgb(255, 219, 219);
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>