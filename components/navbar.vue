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

        <div
          v-if="!$vuetify.breakpoint.xs"
        >
          <v-btn
            text
            plain
            v-for="(route, i) in routes"
            :key="i"
            :to="route.link"
          >
            {{ route.title }}
          </v-btn>
        </div>

        <v-btn
          icon
          :plain="!$vuetify.breakpoint.xs"
          color="transparent"
          @click="toggleTheme()"
        >
          <v-fab-transition
            hide-on-leave
          >
            <img
              src="@/assets/icons/sun.svg"
              alt="facebook"
              height="24"
              width="24"
              v-if="!$vuetify.theme.dark"
            >
          </v-fab-transition>

          <v-fab-transition
            hide-on-leave
          >
            <img
              src="@/assets/icons/moon.svg"
              alt="facebook"
              height="24"
              width="24"
              v-if="$vuetify.theme.dark"
            >
          </v-fab-transition>
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
          color="primary"
        >
          <v-list-item
            v-for="(route, i) in routes"
            :key="i"
            :to="route.link"
          >
            <v-list-item-icon>
              <img
                :src="route.link === $route.path ? route.icon : route.icon_grey"
                height="28"
                width="28"
              >
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title
                v-text="route.title"
                :class="route.link === $route.path ? 'primary--text' : 'grey--text'"
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
  color: #536DFE !important;
}
</style>

<script>
export default({
  data: () => ({
    drawer: false,
    group: null,
    routes: [
      {
        title: 'Home',
        icon: require('@/assets/icons/home.svg'),
        icon_grey: require('@/assets/icons/home-grey.svg'),
        link: "/"
      },
      {
        title: 'About',
        icon: require('@/assets/icons/info.svg'),
        icon_grey: require('@/assets/icons/info-grey.svg'),
        link: "/about"
      },
      {
        title: 'Skills',
        icon: require('@/assets/icons/laptop.svg'),
        icon_grey: require('@/assets/icons/laptop-grey.svg'),
        link: "/skills"
      },
      {
        title: 'Contact',
        icon: require('@/assets/icons/at.svg'),
        icon_grey: require('@/assets/icons/at-grey.svg'),
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
      localStorage.setItem("dark_theme", this.$vuetify.theme.dark.toString());
    }
  },
  mounted() {
    const theme = localStorage.getItem("dark_theme");
    if (theme) {
      if (theme === "true") {
          this.$vuetify.theme.dark = true;
      } else {
          this.$vuetify.theme.dark = false;
      }
    } else if (
      window.matchMedia &&
      window.matchMedia("(prefers-color-scheme: dark)").matches
    ) {
      this.$vuetify.theme.dark = true;
      localStorage.setItem(
          "dark_theme",
          this.$vuetify.theme.dark.toString()
      );
    }
  }
})
</script>
