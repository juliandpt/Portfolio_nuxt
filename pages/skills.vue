<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding-left: 15%; padding-right: 15%' : ''"
  >
    <v-row
      class="mt-8 separation d-flex flex-column justify-center"
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
      class="separation d-flex flex-column justify-center title-wrapper"
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
        <v-card
          loading
          outlined
          :color="!$vuetify.theme.dark ? 'grey lighten-5' : ''"
          height="100%"
        >
          <template 
            slot="progress"
          >
            <v-progress-linear 
              value="100"
            />
          </template>

          <v-card-title>
            <img 
              :src="service.icon"
              height="40"
              width="40"
            />
          </v-card-title>
          
          <v-card-title 
            class="pt-0 font-weight-black"
          >
            {{ service.title }}
          </v-card-title>

          <v-divider 
            class="mx-4"
          />

          <v-card-text
            class="px-4 pb-12"
          >
            {{ service.description }}
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-row
      class="separation d-flex flex-column justify-center"
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
      class="margin"
      v-for="(project, i) in projects"
      :key="i"
    >
      <v-col
        :cols="$vuetify.breakpoint.xs ? '12' : '6'"
        :class="$vuetify.breakpoint.xs ? 'text-center' : ''"
        :order="$vuetify.breakpoint.xs ? '2' : i%2 === 0 ? '1' : '2'"
      >
        <h2
          class="mx-auto my-2 primary--text"
        >
          {{ project.title }}
        </h2>

        <p
          class="my-4"
        >
          {{ project.description }}
        </p>

        <v-btn
          dark
          elevation="0"
          color="primary"
          class="mt-5 mr-auto"
          :href="project.link"
          target="_blank"
          rel="noopener noreferrer"
        >
          See More

          <img
            class="ml-2"
            src="/icons/arrow-white.svg"
            height="18"
            width="18"
          >
        </v-btn>
      </v-col>

      <v-col
        :cols="$vuetify.breakpoint.xs ? '12' : '6'"
        :order="$vuetify.breakpoint.xs ? '1' : i%2 === 0 ? '2' : '1'"
        class="d-flex justify-center align-center shadow"
      >
        <video 
          width='90%'
          muted
          controls
          style="border-radius: 0.35em;"
        >
          <source 
            :src="project.demo" 
            type="video/mp4"
          >

          Your browser does not support the video tag.
        </video>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
.shadow {
  filter: drop-shadow(0 0 3.5em #536DFE)
}

.margin {
  margin-top: 3em;
  margin-bottom: 7em;
}

.separation {
  margin-top: 15%;
  margin-bottom: 3em;
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
            title: "MongoDB",
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
        title: "Web development",
        icon: "/icons/layer.svg",
        description: "I perform modern web pages, having knowledge of Multiple frameworks in a Fullstack development."
      },
      {
        title: "UI / UX",
        icon: "/icons/ux-design.svg",
        description: "I develope the user interface, design web pages and create ux element interactions."
      },
      {
        title: "Software development",
        icon: "/icons/web-programming.svg",
        description: "I develope quality software products, manage software maintenance, and have Knowledge of some of the most popular programming languages."
      },
      {
        title: "Social skills",
        icon: "/icons/people.svg",
        description: "I am an interactive and communicative person, prefering to work in a team instead of alone."
      },
    ],
    projects: [
      {
        title: "Infopueblo",
        description: "Search webapp of Spanish municipalities. It offers leisure data from the different municipalities, compiling the information through web scrapping.",
        link: "https://github.com/juliandpt/Infopueblo",
        demo: "/videos/infopueblo.mp4"
      },
      {
        title: "Webstats",
        description: "Web service responsible for analyzing the security implemented in the different endpoints of any web domain.",
        link: "https://github.com/juliandpt/Webstats",
        demo: "/videos/webstats.mp4"
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