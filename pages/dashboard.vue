<template>
  <v-navigation-drawer
    no-gutters
    permanent
    mini-variant
  >
    <v-list-item
      class="px-2"
    >
      <v-list-item-avatar>
          <v-img
            src="https://randomuser.me/api/portraits/men/85.jpg"
          ></v-img>
      </v-list-item-avatar>
    </v-list-item>

    <v-list dense>
      <v-list-item
        v-for="item in items"
        :key="item.title"
        link
      >
        <v-list-item-icon>
        <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<style scoped>
</style>

<script>
  export default {
    data () {
      return {
        drawer: true,
        items: [
          {
            title: 'Home',
            icon: 'mdi-home-city'
          },
          {
            title: 'My Account',
            icon: 'mdi-account'
          },
          {
            title: 'Users',
            icon: 'mdi-account-group-outline'
          },
        ],
        mini: true,
      }
    },
  }
</script>