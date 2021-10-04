<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding-left: 15%; padding-right: 15%' : ''"
  >
    <v-row
      class="mt-8 mb-4 d-flex flex-column justify-center"
    >
      <h1
        class="mx-auto mb-0"
      >
        Skills
      </h1>

      <p
        class="mx-auto secondary--text"
      >
        My thechnical level
      </p>
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
          <v-expansion-panel
            class="transparent"
          >
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
                  color="primary"
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
                v-for="(card, j) in skill.items"
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
                    color="primary"
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
      class="mt-16 mb-6 d-flex flex-column justify-center title-wrapper"
    >
      <h1
        class="mx-auto mb-0"
      >
        My Services
      </h1>

      <p
        class="mx-auto secondary--text"
      >
        What I offer
      </p>
    </v-row>

    <v-row>
      <v-col
        cols="12"
        md="4"
        sm="6"
        v-for="(service, i) in services"
        :key="i"
        :class="$vuetify.breakpoint.xs ? 'pt-0' : ''"
      >
        <v-hover
          v-slot:default="{ hover }"
        >
          <v-card
            height="100%"
            elevation="0"
            color="transparent"
          >
            <v-flex
              class="pt-4"
            >
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
                color="secondary"
              >
                <v-btn
                  elevation="0"
                  color="primary"
                  @click="showInfo(service)"
                >
                  See more

                  <img
                    src="/icons/arrow.svg"
                    height="18"
                    width="18"
                    class="mr-n1 ml-2"
                  >
                </v-btn>
              </v-overlay>
            </v-fade-transition>
          </v-card>
        </v-hover>
      </v-col>

      <v-dialog
        v-model="dialog"
        max-width="400"
      >
        <v-card>
          <v-card-title
            class="pa-4"
          >
            {{ info.title }}

            <v-spacer></v-spacer>

            <v-btn
              icon
              color="primary"
              @click="dialog = false"
            >
              <v-icon>
                mdi-window-close
              </v-icon>
            </v-btn>
          </v-card-title>

          <v-card-text
            class="px-4"
            v-for="(description, i) in info.descriptions"
            :key="i"
          >
            <div class="d-flex align-center">
              <img
                src="/icons/circle-check.svg"
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
      class="mt-16 mb-6 d-flex flex-column justify-center"
    >
      <h1
        class="mx-auto mb-0"
      >
        My projects
      </h1>

      <p
        class="mx-auto secondary--text"
      >
        The projects I developed
      </p>
    </v-row>

    <v-row
      v-if="!$vuetify.breakpoint.xs"
    >
      <div 
        class="mx-auto"
        :style="$vuetify.breakpoint.sm ? 'min-width: 80%; max-width: 80%;' : 'min-width: 60%; max-width: 60%;'"
      >
        <v-carousel
          cycle
          hide-delimiters
          interval="10000"
          height="300"
        >
          <template
            v-slot:prev="{ on, attrs }"
          >
            <v-btn
              icon
              text
              large
              color="primary"
              v-bind="attrs"
              v-on="on"
            >
              <img
                src="/icons/arrow-prev.svg"
                height="40"
                width="40"
              >
            </v-btn>
          </template>

          <template
            v-slot:next="{ on, attrs }"
          >
            <v-btn
              icon
              text
              large
              color="primary"
              v-bind="attrs"
              v-on="on"
            >
              <img
                src="/icons/arrow-next.svg"
                height="40"
                width="40"
              >
            </v-btn>
          </template>

          <v-carousel-item
            v-for="(project, i) in projects"
            :key="i"
            class="px-16 align-center"
          >
            <v-row
              class="fill-height px-4"
              align="center"
              justify="center"
            >
              <v-card
                elevation="0"
                width="100%"
                :outlined="!$vuetify.theme.dark"
              >
                <v-card-title
                  class="justify-center"
                >
                  {{ project.title }}
                </v-card-title>

                <v-card-text
                  class="secondary--text text-center"
                >
                  {{ project.description }}
                </v-card-text>

                <v-card-actions
                  class="px-4 pb-4"
                >
                  <v-spacer></v-spacer>
                  
                  <v-btn
                    dark
                    elevation="0"
                    color="primary"
                    v-for="(link, j) in project.links"
                    :key="j"
                    :href="link.target"
                    target="_blank"
                  >
                    {{ link.title }}

                    <img
                      src="/icons/link.svg"
                      height="18"
                      width="18"
                      class="mr-n1 ml-2"
                    >
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-row>
          </v-carousel-item>
        </v-carousel>
      </div>
    </v-row>

    <v-row
      v-if="$vuetify.breakpoint.xs"
    >
      <v-col
        cols="12"
        class="pt-0"
        v-for="(project, i) in projects"
        :key="i"
      >
        <v-card
          elevation="0"
          :outlined="!$vuetify.theme.dark"
        >
          <v-card-title>
            {{ project.title }}
          </v-card-title>

          <v-card-text
            class="secondary--text"
          >
            {{ project.description }}
          </v-card-text>

          <v-card-actions
            class="px-4 pb-4"
          >
            <v-spacer></v-spacer>

            <v-btn
              dark
              elevation="0"
              color="primary"
              class="mr-2"
              v-for="(link, j) in project.links"
              :key="j"
              :href="link.target"
              target="_blank"
            >
              {{ link.title }}

              <img
                src="/icons/link.svg"
                height="18"
                width="18"
                class="mr-n1 ml-2"
              >
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style>
.v-window__next, .v-window__prev {
  background: transparent !important
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
    model: null,
    dialog: false,
    info: { },
    skills: [
      {
        title: "Frontend",
        icon: "/icons/tags.svg",
        items: [
          {
            title: "HTML",
            value: 70
          },
          {
            title: "CSS",
            value: 40
          },
          {
            title: "Javascript",
            value: 50
          },
          {
            title: "Angular",
            value: 50
          },
          {
            title: "Vue",
            value: 20
          }
        ]
      },
      {
        title: "Backend",
        icon: "/icons/server.svg",
        items: [
          {
            title: "Node.js",
            value: 50
          },
          {
            title: "Flask",
            value: 50
          },
        ]
      },
      {
        title: "Database",
        icon: "/icons/database.svg",
        items: [
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
            value: 20
          }
        ]
      },
      {
        title: "Others",
        icon: "/icons/brackets.svg",
        items: [
          {
            title: "Python",
            value: 70
          },
          {
            title: "Java",
            value: 40
          },
          {
            title: "C++",
            value: 40
          }
        ]
      },
    ],
    services: [
      {
        title: "SOFTWARE DEVELOPMENT",
        icon: "/icons/web-programming.svg",
        descriptions: [
          "I develop the user interface.",
          "Web page design.",
          "I create ux element interactions."
        ]
      },
      {
        title: "UI / UX",
        icon: "/icons/ux-design.svg",
        descriptions: [
          "I develop the user interface.",
          "Web page design.",
          "I create ux element interactions."
        ]
      },
      {
        title: "WEB DEVELOPMENT",
        icon: "/icons/speedometer.svg",
        descriptions: [
          "caca1",
          "caca2"
        ]
      },
      {
        title: "TEAM WORK",
        icon: "/icons/team.svg",
        descriptions: [
          "caca1",
          "caca2"
        ]
      },
    ],
    projects: [
      {
        title: "Infopueblo",
        description: "Webapp to collect information through web scraping, and classification of Emptied Spain by machine learning of Spanish municipalities.",
        links: [
          {
            title: "Front-end",
            target: "https://github.com/juliandpt/Infopueblo-Frontend"
          },
          {
            title: "Back-end",
            target: "https://github.com/juliandpt/Infopueblo-Backend"
          }
        ]
      },
      {
        title: "Ada 2012 Compiler",
        description: "Basic compiler for Ada 2012 using Flex and Bison.",
        links: [
          {
            title: "See more",
            target: "https://github.com/juliandpt/Compilador"
          }
        ]
      },
    ],
  }),
  methods: {
    showInfo (data) {
      this.info = data
      this.dialog = true
    }
  }
};
</script>