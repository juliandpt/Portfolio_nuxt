<template>
  <div
    class="glass"
  >
    <v-card
      flat
      color="transparent"
    >
      <v-container>
        <v-app-bar
          flat
          plain
          color="transparent"
        >
          <v-btn
            icon
            text
            large
            :color="$vuetify.theme.dark ? 'white' : 'black'"
            v-if="$vuetify.breakpoint.xs"
            @click.stop="drawer = !drawer"
          >
            <img
              src="/icons/bars-white.svg"
              alt="bars-white"
              height="24"
              width="24"
              v-if="$vuetify.theme.dark"
            >

            <img
              src="/icons/bars-black.svg"
              alt="bars-black"
              height="24"
              width="24"
              v-else
            >
          </v-btn>

          <img 
            src="/favicon.ico"
            alt="icon"
            :class="$vuetify.breakpoint.xs ? 'ml-3 d-flex align-center' : 'd-flex align-center'"
            :height="$vuetify.breakpoint.xs ? '24' : '50'"
            width="auto"
          />
          
          <v-spacer />

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

          <v-spacer />

          <v-btn
            icon
            color="transparent"
            :plain="!$vuetify.breakpoint.xs"
            @click="toggleTheme()"
          >
            <v-fab-transition
              hide-on-leave
            >
              <img
                src="/icons/sun.svg"
                alt="sun"
                height="24"
                width="24"
                v-if="!$vuetify.theme.dark"
              >
            </v-fab-transition>

            <v-fab-transition
              hide-on-leave
            >
              <img
                src="/icons/moon.svg"
                alt="moon"
                height="24"
                width="24"
                v-if="$vuetify.theme.dark"
              >
            </v-fab-transition>
          </v-btn>
        </v-app-bar>
      </v-container>
    </v-card>

    <v-navigation-drawer
      app
      absolute
      temporary
      v-model="drawer"
      v-if="$vuetify.breakpoint.xs"
    >
      <v-list
        flat
      >
        <v-list-item-group
          color="primary"
        >
          <v-btn
            icon
            text
            x-large
            color="secondary"
            v-if="$vuetify.breakpoint.xs"
            @click.stop="drawer = !drawer"
          >
            <img
              src="/icons/close-grey.svg"
              alt="close-grey"
              height="24"
              width="24"
            >
          </v-btn>

          <v-list-item
            v-for="(route, i) in routes"
            :key="i"
            :to="route.link"
          >
            <v-list-item-icon>
              <img
                :src="route.link === $route.path ? route.icon : route.icon_grey"
                :alt="route.alt"
                height="28"
                width="28"
              >
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title
                v-text="route.title"
                :class="route.link === $route.path ? 'primary--text' : 'secondary--text'"
              ></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<style lang="scss">
.v-btn--active {
  background-color: transparent !important;
  color: #536DFE !important;
}

.glass {
  backdrop-filter: blur(12px);
  position: sticky;
  top: 0;
  z-index: 50;
}
</style>

<script>
export default({
  data: () => ({
    drawer: false,
    group: null,
    routes: [
      {
        title: "Home",
        icon: "/icons/home.svg",
        icon_grey: "/icons/home-grey.svg",
        alt: "home",
        link: "/"
      },
      {
        title: "About",
        icon: "/icons/info.svg",
        icon_grey: "/icons/info-grey.svg",
        alt: "about",
        link: "/about"
      },
      {
        title: "Skills",
        icon: "/icons/laptop.svg",
        icon_grey: "/icons/laptop-grey.svg",
        alt: "skills",
        link: "/skills"
      },
      {
        title: "Contact",
        icon: "/icons/at.svg",
        icon_grey: "/icons/at-grey.svg",
        alt: "contact",
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