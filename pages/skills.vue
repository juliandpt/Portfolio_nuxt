<template>
  <v-container
    :style="$vuetify.breakpoint.xl ? 'padding: 0 15%' : ''"
  >
    <v-row
      class="py-8"
    >
      <h1
        class="mx-auto"
      >
        My Skills
      </h1>
    </v-row>
      
    <v-row>
      <v-col
        cols="12"
        sm="6"
        xs="12"
        v-for="(skill, i) in skills"
        :class="$vuetify.breakpoint.xs ? 'pb-0' : ''"
        :key="i"
      >
        <v-expansion-panels
          flat
        >
          <v-expansion-panel>
            <v-expansion-panel-header>
              <div class="d-flex align-center">
                <img
                  :src="skill.icon"
                  height="32"
                  width="32"
                  class="pa-0 mr-3"
                >

                {{ skill.title }}
              </div>
              

              <template v-slot:actions>
                <v-icon color="indigo">
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
        Specialized in
      </h1>
    </v-row>

    <v-row>
      <v-col
        cols="12"
        md="4"
        sm="6"
        xs="12"
        v-for="(specialty, i) in specialties"
        :class="$vuetify.breakpoint.xs ? 'pb-0' : ''"
        :key="i"
      >
        <v-card
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
        md="4"
        sm="6"
        xs="12"
        v-for="(service, i) in services"
        :class="$vuetify.breakpoint.xs ? 'pb-0' : ''"
        :key="i"
      >
        <v-card
          flat
          class="d-flex flex-column align-center"
        >
          <v-img
            :src="service.icon"
            height="64"
            width="64"
            class="ma-4"
          ></v-img>

          <v-card-title>
            {{ service.title }}
          </v-card-title>

          <v-card-text>
            {{ service.text }}
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  head() {
    return {
      title: "Skills"
    }
  },
  data() {
    return {
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
          text: "caca tambien"
        },
        {
          title: "RESPONSIVE DESIGN",
          icon: require("@/assets/icons/responsive.svg"),
          text: "caca tambien"
        },
        {
          title: "UI / UX",
          icon: require("@/assets/icons/crosshair.svg"),
          text: "caca tambien"
        },
        {
          title: "WEB DEVELOPMENT",
          icon: require("@/assets/icons/settings.svg"),
          text: "caca tambien"
        },
      ]
    }
  }
};
</script>