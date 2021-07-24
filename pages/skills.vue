<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding-left: 15%; padding-right: 15%' : ''"
  >
    <v-row
      class="d-flex flex-column justify-center py-8"
    >
      <h1
        class="mx-auto"
      >
        Skills
      </h1>

      <h4
        class="mx-auto"
      >
        My thechnical level
      </h4>
    </v-row>
      
    <v-row>
      <v-col
        cols="12"
        sm="6"
        v-for="(skill, i) in skills"
        :key="i"
        :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
      >
        <v-expansion-panels
          flat
        >
          <v-expansion-panel>
            <v-expansion-panel-header>
              <div
                class="d-flex align-center"
              >
                <img
                  :src="skill.icon"
                  height="32"
                  width="32"
                  class="pa-0 mr-3"
                >

                {{ skill.title }}
              </div>

              <template
                v-slot:actions
              >
                <v-icon
                  color="indigo"
                >
                  $expand
                </v-icon>
              </template>
            </v-expansion-panel-header>

            <v-expansion-panel-content>
              <v-card
                flat
                tile
                color="transparent"
                v-for="(card, j) in skill.cards"
                :key="j"
              >
                <v-card-title
                  class="px-0"
                >
                  <template
                    class="d-flex"
                  >
                    <p
                      class="ma-0"
                    >
                      {{ card.title }}
                    </p>

                    <p
                      class="ml-auto ma-0"
                    >
                      {{ card.value }}%
                    </p>
                  </template>
                </v-card-title>

                <v-card-text
                  class="px-0"
                >
                  <v-progress-linear
                    rounded
                    color="indigo"
                    :value="card.value"
                  ></v-progress-linear>
                </v-card-text>
              </v-card>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-col>
    </v-row>

    <v-row
      class="py-8"
    >
      <h1
        class="mx-auto"
      >
        Specialing in
      </h1>
    </v-row>

    <v-row>
      <v-col
        cols="12"
        md="4"
        sm="6"
        v-for="(specialty, i) in specialties"
        :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
        :key="i"
      >
        <v-card
          flat
          dark
          color="indigo"
        >
          <v-card-title>
            {{ specialty.title }}
          </v-card-title>

          <v-card-text>
            {{ specialty.text }}
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-row
      class="py-8"
    >
      <h1
        class="mx-auto"
      >
        My Services
      </h1>
    </v-row>

    <v-row>
      <v-col
        cols="12"
        md="3"
        sm="6"
        v-for="(service, i) in services"
        :key="i"
        :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
      >
        <v-hover
          v-slot:default="{ hover }"
        >
          <v-card
            outlined
            height="100%"
          >
            <v-flex class="pt-4">
              <v-img
                :src="service.icon"
                height="64"
                width="64"
                class="mx-auto"
              ></v-img>
            </v-flex>

            <v-card-title
              class="justify-center pb-auto"
            >
              {{ service.title }}
            </v-card-title>

            <v-fade-transition>
              <v-overlay
                v-if="hover"
                absolute
                :color="$vuetify.theme.dark ? 'grey darken-4' : 'indigo lighten-5'"
              >
                <v-btn
                  color="indigo"
                  @click="showInfo(service)"
                >
                  view more
                </v-btn>
              </v-overlay>
            </v-fade-transition>
          </v-card>
        </v-hover>
      </v-col>

      <v-dialog
        v-model="dialog"
        width="325"
      >
        <v-card>
          <v-card-title
            class="pr-3"
          >
            {{ info.title }}

            <v-spacer></v-spacer>

            <v-btn
              icon
              color="indigo"
              @click="dialog = false"
            >
              <v-icon>
                mdi-window-close
              </v-icon>
            </v-btn>
          </v-card-title>

          <v-card-text
            v-for="(description, i) in info.descriptions"
            :key="i"
          >
            <div class="d-flex align-center">
              <img
                src="@/assets/icons/check.svg"
                height="18"
                width="18"
                class="pa-0 mr-3"
              >

              {{ description }}
            </div>
          </v-card-text>
        </v-card>
      </v-dialog>
    </v-row>

    <v-row
      class="py-8"
    >
      <h1
        class="mx-auto"
      >
        My projects
      </h1>
    </v-row>

    <v-row>
      <v-col
        cols="12"
        md="3"
        sm="6"
        v-for="(project, i) in projects"
        :key="i"
        :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
      >
        <v-card
          class="mx-auto"
        >
          <v-img
            :src="$vuetify.theme.dark ? project.imgWhite : project.img"
            width="200"
            class="align-center justify-center"
          ></v-img>

          <v-card-title>
            {{ project.title }}
          </v-card-title>

          <v-card-subtitle>
            {{ project.content }}
          </v-card-subtitle>

          <v-card-actions>
            <v-spacer></v-spacer>

            <v-btn
              color="orange lighten-2"
              text
            >
              Explore
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style lang="scss" scoped>
h1 {
  font-size: 3.5rem;
  margin-bottom: 1rem;
}

h4 {
  color: #9E9E9E;
  margin-bottom: 20px;
}
</style>

<script>
export default {
  head() {
    return {
      title: "Skills"
    }
  },
  data: () => ({
    skills: [
      {
        title: "Frontend",
        icon: require("@/assets/icons/tags.svg"),
        cards: [
          {
            title: "HTML",
            value: 70
          },
          {
            title: "CSS",
            value: 60
          },
          {
            title: "Javascript",
            value: 70
          },
          {
            title: "Angular",
            value: 70
          },
          {
            title: "Vue",
            value: 20
          }
        ]
      },
      {
        title: "Backend",
        icon: require("@/assets/icons/server.svg"),
        cards: [
          {
            title: "Node",
            value: 70
          },
          {
            title: "Flask",
            value: 70
          },
        ]
      },
      {
        title: "Database",
        icon: require("@/assets/icons/database.svg"),
        cards: [
          {
            title: "MariaDB",
            value: 70
          },
          {
            title: "PostgreSQL",
            value: 70
          },
          {
            title: "Firebase",
            value: 60
          }
        ]
      },
      {
        title: "Others",
        icon: require("@/assets/icons/brackets.svg"),
        cards: [
          {
            title: "Python",
            value: 70
          },
          {
            title: "Java",
            value: 70
          },
          {
            title: "C++",
            value: 60
          }
        ]
      },
    ],
    specialties: [
      {
        title: "FRONT-END DEV",
        text: "caca tambien"
      },
      {
        title: "FRONT-END DEV",
        text: "caca tambien"
      },
      {
        title: "FRONT-END DEV",
        text: "caca tambien"
      }
    ],
    services: [
      {
        title: "WEB DESIGN",
        icon: require("@/assets/icons/design.svg"),
        text: "caca tambien",
        descriptions: [
          "caca1",
          "caca2",
          "caca3"
        ]
      },
      {
        title: "RESPONSIVE DESIGN",
        icon: require("@/assets/icons/responsive.svg"),
        text: "caca tambien",
        descriptions: [
          "caca1",
          "caca2",
          "caca3"
        ]
      },
      {
        title: "UI / UX",
        icon: require("@/assets/icons/crosshair.svg"),
        text: "caca tambien",
        descriptions: [
          "caca1",
          "caca2",
          "caca3"
        ]
      },
      {
        title: "WEB DEVELOPMENT",
        icon: require("@/assets/icons/settings.svg"),
        text: "caca tambien",
        descriptions: [
          "caca1",
          "caca2"
        ]
      },
    ],
    projects: [
      {
        title: "Infopueblo",
        img: require("@/assets/images/infopueblo.png"),
        imgWhite: require("@/assets/images/infopueblo-white.png"),
        content: "cacadevaca",
        repository: "https://github.com/julidpt/Infopueblo-Frontend"
      },
      {
        title: "Infopueblo",
        img: require("@/assets/images/infopueblo-white.png"),
        content: "cacadevaca",
        repository: "https://github.com/julidpt/Infopueblo-Frontend"
      }
    ],
    info: { },
    dialog: false
  }),
  methods: {
    showInfo (data) {
      this.info = data
      this.dialog = true
    }
  }
};
</script>