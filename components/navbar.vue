<template>
  <v-container>
    <v-card
      flat
      color="transparent"
    >
      <v-app-bar
        flat
        plain
        color="transparent"
      >
        <v-app-bar-nav-icon
          v-if="$vuetify.breakpoint.xs"
          @click.stop="drawer = !drawer"
        ></v-app-bar-nav-icon>

        <v-toolbar-title
          class="pa-0"
        >
          Julián de Pablo
        </v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn
          text
          plain
          to="/"
          v-if="!$vuetify.breakpoint.xs"
          style="textTransform: none; letter-spacing: 0;"
        >
          Home
        </v-btn>

        <v-btn
          text
          plain
          to="/about"
          v-if="!$vuetify.breakpoint.xs"
          style="textTransform: none; letter-spacing: 0;"
        >
          About
        </v-btn>

        <v-btn
          text
          plain
          to="/skills"
          v-if="!$vuetify.breakpoint.xs"
          style="textTransform: none; letter-spacing: 0;"
        >
          Skills
        </v-btn>

        <v-btn
          text
          plain
          to="/contact"
          v-if="!$vuetify.breakpoint.xs"
          style="textTransform: none; letter-spacing: 0;"
        >
          Contact
        </v-btn>

        <v-btn
          icon
          plain
          color="black"
          v-if="!$vuetify.theme.dark"
          @click="toggleTheme()"
        >
          <img
            src="@/assets/icons/moon-dark.svg"
            alt="facebook"
            height="24"
            width="24"
          >
        </v-btn>

        <v-btn
          icon
          plain
          color="white"
          v-else
          @click="toggleTheme()"
        >
          <img
            src="@/assets/icons/sun-white.svg"
            alt="facebook"
            height="30"
            width="30"
          >
        </v-btn>
      </v-app-bar>
    </v-card>

    <v-navigation-drawer
      absolute
      temporary
      v-model="drawer"
      v-if="$vuetify.breakpoint.xs"
    >
      <v-list flat>
        <v-list-item-group
          v-model="selectedItem"
          color="indigo"
        >
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            :to="item.link"
          >
            <v-list-item-icon>
              <img
                :src="item.icon"
                height="28"
                width="28"
              >
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title
                v-text="item.title"
              ></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </v-container>
</template>

<style lang="scss">
.v-btn--active {
  background-color: transparent !important;
  color: #3f51b5 !important;
}

.v-input__control {
  margin: 0 0 0 0.5em;
}
</style>

<script>
export default({
  data: () => ({
    drawer: false,
    group: null,
    selectedItem: 0,
    items: [
      {
        title: 'Home',
        icon: require('@/assets/icons/home.svg'),
        link: "/"
      },
      {
        title: 'About',
        icon: require('@/assets/icons/info.svg'),
        link: "/about"
      },
      {
        title: 'Skills',
        icon: require('@/assets/icons/laptop.svg'),
        link: "/skills"
      },
      {
        title: 'Contact',
        icon: require('@/assets/icons/at.svg'),
        link: "/contact"
      },
    ],
  }),
  watch: {
    group () {
      this.drawer = false
    },
  },
  methods: {
    toggleTheme: function () {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    }
  }
})
</script>
